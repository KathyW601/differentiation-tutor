# differentiation-tutor
import sympy as sp
x=sp.symbols('x')
steps=[]
equation_input=input("please enter a function with variable x, for example(x**2+2*x+4)")
equation=sp.sympify(equation_input)
if any(term.is_constant() for term in sp.Add.make_args(equation)):
  steps.append("you need to use constant rule, and the derivative of the constant is 0")
if equation.has(sp.Pow):
  if any(term.as_base_exp()[1]==-1 for term in sp.preorder_traversal(equation)):
    steps.append("you need to use the quotient rule")
  else:
    steps.append("you need to use power rule")
if equation.has(sp.Mul):
  steps.append("you need to use the product rule")
if equation.has(sp.Function):
  steps.append("you need to use the chain rule")
derivative=sp.diff(equation,x)
print("the derivative of the function is",derivative)
print("the process of differentiation")
for n in steps:
  print(n)

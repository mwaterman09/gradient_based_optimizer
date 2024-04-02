# Directed_gradient_optimizer
The purpose of this project is to experiment with developing a gradient-based optimizer that is capable of "seeing" over saddle points and other situations which may cause the traditional gradient descent algorithm to fail to converge on the global minimum. It aims to add an inherent adaptive learning rate based on selecting minimum points along a directed line segment.  

My approach is to use the gradient as a directional guide and generate points along a line starting from a random initial point and iteratively generate new lines from the coordinates of the minimum value of the previous line. The steps to the algorithm are as follows:  

1) Generate random inital point $p_0$ coordinates on the surface of the objective function
2) Calculate the angle $\theta_0$ of the gradient at $p_0$ by using $\arctan(\frac{\nabla{F_y}}{\nabla{F_x}})$
3) Generate a line of length ```search_radius``` from the initial point in the direction of $\theta_0$
4) Evaluate the minimum value of the function along that line and save the coordinates of this min value as $p_1$
5) Calculate the new angle $\theta_1$ of the gradient at $p_1$
6) Repeat the process ```iterations``` times
   
The algorithm is named "Lagrange descent" because the shape of the line is determined by the Euler-Lagrange (EL) equations 

$$ \frac{\partial L}{\partial x^\alpha} - \frac{d}{d\lambda}\frac{\partial L}{\partial \frac{dx}{d\lambda}} =0 $$  

with the goal of applying it to a wide variety of objective functions. In the case of the example objective function $z = x^2 + y^2$, the EL equations reduce to the gradient and the minimizing path between two points is a straight line.

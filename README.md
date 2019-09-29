# FitCircle_LeastSquareMethod

/* A circle solver by transforming the standard circle equation to a linear system and then applying Least Square Method

    The standard equation of a circle is shown below
    (xi-x0)^2+(yi-y0)^2 = r^2           (i=1,2...,n)
    where, x0 and y0 are center coordinate (x0, y0) of the unknown circle, and r is the radius of the circle
                points (xi,yi) are used to fit the unknown circle

    The equation can be rewritten as below
    2*xi*x0 + 2*yi*y0 + (r^2-x0^2-y0^2) = xi^2+yi^2         (i=1,2...,n)

    Suppose C = (r^2-x0^2-y0^2), we can get
    2*xi*x0 + 2*yi*y0 + C = xi^2+yi^2         (i=1,2...,n)

    Therefore, we can rewrite the above equation with matrix
    AX = Y,
    where A = [2x1    2y1    1;
                       2x2    2y2    1;
                       ...       ...       ...;
                       2xn    2yn    1]

               X = [x0;y0;C]

               Y = [x1^2+y1^2;
                       x2^2+y2^2;
                               ...
                       xn^2+yn^2;]

    Finally, X = (A.transpose()*A).inverse()*A.transpose()*Y,
                                 [A11,A12, A13;
    A.transpose()*A = A21, A22, A23;
                                 A31, A32, A33]
    with, A11 = 4*sum(xi^2);
            A12 = 4*sum(xi*yi);
            A13 = 2*sum(xi);
            A21 = A12;
            A22 = 4*sum(yi^2);
            A23 = 2*sum(yi);
            A31 = A13
            A32 = A23;
            A33 = n
*/

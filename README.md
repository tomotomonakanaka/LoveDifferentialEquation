#LoveDifferentialEquation
## Abstract
Differential Equation is a powerful tool to model how systems change over time. In this paper, I propose the differential equation architectures for love and see this model simulates the love dynamics well. Previous research suggested the linear differential equation model for love between two people. Here, I generalize this model to the loves between the n people and incorporate the idea of popularity, gender, and capacity into this model, which are impossible to consider in two people’s love. Also, I will show this initial problem is well posed.


\section{Model}
To construct the model, first we define the feeling from i to j. Let us denote the i's feeling to j at time t by $x_{i,j}(t)$. Now, we assume that the change of i's feeling only depends on the feeling from i to j and the feeling from j to i. The ordinary differential equation is written like

\begin{equation}
 \frac{dx_{i,j}}{dt} = \alpha_{i,j} x_{i,j} + \beta_{i,j} x_{j,i}
 \label{eq:one}
\end{equation}
which is naturally induced from Eq.~(\ref{eq:one}).
$\alpha_{i,j}$ and $\beta_{i,j}$ are constants and defined by popularity and love constitution.

\subsection{Popularity}
To model the popularity of the person, we define
\begin{equation}
 \alpha_{i,j} = \alpha_{i,j}' + p_{j}
 \label{eq:two}
\end{equation}
\begin{equation}
 \beta_{i,j} = \beta_{i,j}' + p_{j}
 \label{eq:three}
\end{equation}
$\alpha_{i,j}'$ and $\beta_{i,j}'$ are i's love constitution, and $p_{j}$ is the popularity of j. If $p_{j}$ is big then j's popularity is high.

\subsection{Capacity}
In the real world, people cannot love all people. Therefore, we introduce the concept of capacity of love to this model.
\begin{equation}
 \frac{dx_{i,j}}{dt} = \alpha_{i,j} x_{i,j} + \beta_{i,j} x_{j,i} + sgn(x_{i,j})\gamma_{i,j}(1-|x_i|)
 \label{eq:four}
\end{equation}
where $|x_i| = \sqrt{\sum_j x_{i,j}^2}$ and $\gamma_{i,j}$ is a constant.

\subsection{Gender}
To model gender, we initialize $x_{i,j}$ as
\begin{equation}
  x^{(0)}_{i,j}= \begin{cases}
    0 & (g(i) = g(j)) \\
    f_{i,j} & (otherwise)
  \end{cases}
\end{equation}
where
\begin{equation}
  g(k) = \begin{cases}
    0 & (k\ is\ male) \\
    1 & (k\ is\ female)
  \end{cases}
\end{equation}
\subsection{The Definition of Falling in Love}
\subsection{Matrix Form}
\begin{equation}
    \frac{dX}{dt} = A\otimes X + B\otimes X^T + sgn(X) \otimes \Gamma \otimes (\textbf{1}-X_2)
\end{equation}
where
$X_{i,j} = x_{i,j}$, $sgn(X)_{i,j} = sgn(x_{i,j})$, $A_{i,j} = \alpha_{i,j}$
, $B_{i,j} = \beta$
, $\Gamma_{i,j} = \gamma_{i,j}$, $X_{2,i,j} = |x_i|$

\name{parallel QPADM-slack}
\title{Penalized quantile regression Using the Slack Variable Representation}
\usage{
QPADMslackpara(eps, y, x, betatrue, tau, lambda, a, pho, K, funname, maxstep)
}
\arguments{
\item{eps}{The terminate condition}

\item{y}{The response vector}

\item{x}{The design matrix (with intercept)}

\item{betatrue}{The real value of the coefficient}

\item{tau}{The quantile of interest}

\item{lambda}{The penalization parameter}

\item{a}{The shape parameter for the SCAD/MCP penalty}

\item{pho}{The augmentation parameter for the ADMM}

\item{K}{The number of partitions}

\item{funname}{Name of the penalty to use, currently support ("scad","mcp")}

\item{maxstep}{Maximum number of iterations allowed}
}
\value{
The absolute estimation error of the coefficient

The number of iterations

The running time
}
\description{
This is a parallel implementation. 
}
\examples{
n = 300000
p = 100
K = 100
beta_true = rep(0, p)
beta_true[1] = 0.7*qnorm(0.3)
beta_true[6] = beta_true[12] = beta_true[15] = beta_true[20] = 1
set.seed(66)
X = matrix(rnorm(n*p),nrow=n) 
cov = gcov(p, rho)
X = X%*%chol(cov)
X[,1] = pnorm(X[,1])
e = rnorm(n)
Y = X[,6]+X[,12]+X[,15]+X[,20]+0.7*X[,1]*e
QPADMslackpara_scad = QPADMslackpara(1e-03, Y, X, beta_true, 0.3, 30, 3.7, 1, K, "scad", 500)
AE = QPADMslackpara_scad[1]
time = QPADMslackpara_scad[2]
step = QPADMslackpara_scad[3]
}

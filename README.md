# utl-find-the-first-set-of-column-sums-that-sum-to-twenty-one-using-r-linear-programming-lpsolve
Find the first set of column sums that sum to twenty one using r linear programming lpsolve
    %let pgm=utl-find-the-first-set-of-column-sums-that-sum-to-twenty-one-using-r-linear-programming-lpsolve;

    %stop_submission;

    Find the first set of column sums that sum to twenty one using r linear programming lpsolve

    github
    https://tinyurl.com/4jzwk2df
    https://github.com/rogerjdeangelis/utl-find-the-first-set-of-column-sums-that-sum-to-twenty-one-using-r-linear-programming-lpsolve

    related to
    https://communities.sas.com/t5/Mathematical-Optimization/OptModel-to-find-a-variance-in-a-table/m-p/760505#M3471

    Related repos

    https://tinyurl.com/2xvk7582
    https://github.com/rogerjdeangelis/utl-minimize-cost-of-cattle-feed-with-nutritional-requirements-and-multiple-food-sources-lp-progr

    https://tinyurl.com/cpd6nh39
    https://github.com/rogerjdeangelis/utl-optimum-number-of-ten-cm-rods-to-cut-into-toy-trains-and-hot-wheels-axles-lp-linear-programmi

    https://tinyurl.com/5cbzkbve
    https://github.com/rogerjdeangelis/utl-simple-linear-programming-example-using-R-and-sas-dual-simplex

    https://tinyurl.com/yj8yejfh
    https://github.com/rogerjdeangelis/utl-using-instrumental-variables-to-more-precisely-predict-the-income-of-vietnam-veterans

    /**************************************************************************************************************************/
    /* INPUT                          |  PROCESS                                       |  OUTPUT                              */
    /* =====                          |  =======                                       |  ======                              */
    /* options validvarname=upcase;   |  Find the first column sums                    |  > R                                 */
    /* libname sd1 "d:/sd1";          |  that sum to 21                                |    selected_cols                     */
    /* data sd1.have;                 |                                                |  1             1                     */
    /*  input x1-x7;                  |  X1 X2 X3 X4 X5 X6 X7                          |  2             2                     */
    /*  format x1-x7 z2.;             |                                                |  3             3                     */
    /* cards4;                        |   1  0  3  0  7 11  0                          |                                      */
    /* 1 0 3 0 7 11 0 0               |   2  0  3  5  0  0 13                          |  SAS                                 */
    /* 2 0 3 5 0 0 13 0               |   3  1  0  0  7  0 13                          |                                      */
    /* 3 1 0 0 7 0 13 0               |   4  1  3  0  0  0  0                          |  SELECTED_                           */
    /* 4 1 3 0 0 0 0 17               |                                                |     COLS                             */
    /* ;;;;                           |  10  2  9  5 14 11 26                          |                                      */
    /* run;quit;                      | |--------|                                     |      1                               */
    /*                                |                                                |      2                               */
    /*                                | 10=2+9=21 so set=x1-x3                         |      3                               */
    /*                                |                                                |                                      */
    /*                                | proc datasets                                  |                                      */
    /*                                |    lib=sd1 nolist                              |                                      */
    /*                                |    nodetails;                                  |                                      */
    /*                                |  delete want;                                  |                                      */
    /*                                | run;quit;                                      |                                      */
    /*                                |                                                |                                      */
    /*                                | %utl_rbeginx;                                  |                                      */
    /*                                | parmcards4;                                    |                                      */
    /*                                | library(haven)                                 |                                      */
    /*                                | library(lpSolve)                               |                                      */
    /*                                | library(sqldf)                                 |                                      */
    /*                                | source("c:/oto/fn_tosas9x.R")                  |                                      */
    /*                                | options(sqldf.dll = "d:/dll/sqlean.dll")       |                                      */
    /*                                | mat<-read_sas("d:/sd1/have.sas7bdat")          |                                      */
    /*                                | print(mat)                                     |                                      */
    /*                                | colsum <- colSums(mat)                         |                                      */
    /*                                | objective <- rep(0, length(colsum))            |                                      */
    /*                                | const.mat <- rbind(colsum)                     |                                      */
    /*                                | const.dir <- "="                               |                                      */
    /*                                | const.rhs <- 21                                |                                      */
    /*                                | result <- lp(                                  |                                      */
    /*                                |      "min"                                     |                                      */
    /*                                |      ,objective                                |                                      */
    /*                                |      ,const.mat                                |                                      */
    /*                                |      ,const.dir                                |                                      */
    /*                                |      ,const.rhs                                |                                      */
    /*                                |      ,all.bin=TRUE)                            |                                      */
    /*                                |                                                |                                      */
    /*                                | if (result$status == 0) {                      |                                      */
    /*                                |   selected_cols<-which(result$solution==1)     |                                      */
    /*                                |   print(selected_cols)                         |                                      */
    /*                                | } else {                                       |                                      */
    /*                                |   print("No combination found")                |                                      */
    /*                                | }                                              |                                      */
    /*                                | want<-data.frame(selected_cols)                |                                      */
    /*                                | want;                                          |                                      */
    /*                                | fn_tosas9x(                                    |                                      */
    /*                                |       inp    = want                            |                                      */
    /*                                |      ,outlib ="d:/sd1/"                        |                                      */
    /*                                |      ,outdsn ="want"                           |                                      */
    /*                                |      )                                         |                                      */
    /*                                | ;;;;                                           |                                      */
    /*                                | %utl_rendx;                                    |                                      */
    /*                                |                                                |                                      */
    /*                                | proc print data=sd1.want;                      |                                      */
    /*                                | run;quit;                                      |                                      */
    /**************************************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */

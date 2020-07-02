# Database
In this repository, we collect data on line bundle cohomologies over curves in a del Pezzo surface of degree 6. This data was analyzed in our [publication](https://arxiv.org/abs/2007.00009) using Decision Trees. The so-obtained insights, supplemented and extended by a working understanding of the corresponding algebraic geometry, lead to the software [H0Approximator](https://github.com/homalg-project/ToricVarieties_project/tree/master/H0Approximator).

# How to read the CSV files
We have computed line bundle cohomologies for line bundles of different degrees over curves of different genera. The curves and line bundles are specified as follows:
A del Pezzo surface is a complex two-dimensional surface obtained from blowing up the complex projective space CP^2 in three points in general position. We denote the hyperplane class of CP^2 by *H* and the divisor classes of the three blowup divisors by *E_1*, *E_2*, and *E_3*, respectively. A curve inside the del Pezzo surface given as a section of *a H + b E_1 + c E_2 + d E_3* is then specified as *D_C=(a;b,c,d)*. Similarly, we specify a line bundle *L* by giving the first Chern class of the bundle for each divisor class, *D_L=(a';b',c',d')*.
The folders in this repository are organized by the genus of the curve, with subfolders for the individual line bundles.

## Folder structure
Folder|Description
------|-----------
[./Genus-1](Genus-1)|A genus one curve with *D_C=(3;-1,-1,-1)*. This curve has 7 monomials. We compute data for 13 different line bundles.
[./Genus-1-2](Genus-1-2)|A disjoint union of a genus 0 and genus 2 curve genus one curve with *D_C=(4;-1,-2,1)*. This curve has 11 monomials. We compute data for 13 different line bundles.
[./Genus-2](Genus-2)|A genus two curve with *D_C=(4;-1,-2,-1)*. This curve has 10 monomials. We compute data for 13 different line bundles.
[./Genus-2-2](Genus-2-2)|A genus two curve with *D_C=(4;-1,-2,0)*. This curve has 11 monomials. We compute data for 1 line bundle.
[./Genus-2-3](Genus-2-3)|Two genus two curves. The first is *D_C=(3;-3,-1,-2)*. This curve has 10 monomials. We compute data for 1 line bundle. The second is *D_C=(4;-7,-1,-3)*. This curve has 10 monomials. We compute data for 1 line bundle.
[./Genus-3](Genus-3)|A genus three curve with *D_C=(4;-1,-1,-1)*. This curve has 12 monomials. We compute data for 13 different line bundles.
[./Genus-4](Genus-4)|A genus four curve with *D_C=(5;-2,-2,-1)*. This curve has 14 monomials. We compute data for 13 different line bundles.
[./Genus-5](Genus-5)|A genus five curve with *D_C=(5;-1,-1,-2)*. This curve has 16 monomials. We compute data for 13 different line bundles.
[./Genus-6](Genus-6)|A genus five curve with *D_C=(6;-3,-2,-1)*. This curve has 18 monomials. We compute data for 2 different line bundless.

Each folder contains a file `CurveData.csv` and subfolders (one for each line bundle). Each subfolder will contain a `SummaryOfResults` folder with a file `ResultsWithSplitIntersectionsPlusLocalSections.csv`.

## Structure of CurveData.csv
Here we explain what the different columns of the `CurveData.csv` file mean:

Column|Description
------|-----------
coeffs|Array specifying the values of the coefficients that appear in front of the monomials that define the curve inside the del Pezzo surface. We compute data for all *c_i* in {0,1} (except for the Genus-2-3 curves, where we take them from {-1,0,1}), a curve with *m* monomials has *2^(m)* different combinations of coefficients. We exclude the case where all coefficients are zero
curve-smooth|TRUE if the curve with the corresponding coefficients is smooth, FALSE otherwise
curve-split-number|The number of components the curve splits into
splits-reduced|For each component that the curves splits into, this specifies whether the component is reduced (True) or not (False)
splits-smooth|For each component that the curves splits into, this specifies whether the component is smooth (True) or not (False)
splits-genera|For each component that the curves splits into, this specifies genus of the split component
splits-intersections|This is the intersection matrix of the split components
splits-classes|This assigns classes to the different split types. This data is used to check whether different splits actually agree
split-type|An integer labeling the type of splits built from various topological invariants. See the paper for more details
determinant|The determinant of the intersection matrix. This is, up to a sign, permutation invariant and is used to distinguish different splits
split-type2|Another integer labeling the type of splits built from various topological invariants. We used this integer for the decision trees. See the paper for more details

## Structure of ResultsWithSplitIntersectionsPlusLocalSections.csv
Here we explain what the different columns of the `ResultsWithSplitIntersectionsPlusLocalSections.csv` file mean:

Column|Description
------|-----------
coeffs|Array specifying the values of the coefficients that appear in front of the monomials that define the curve inside the del Pezzo surface. We compute data for all *c_i* in {0,1} 
curve|Specification of the curve *D_C=(a;b,c,d)* as explained above
bundle|Specification of the bundle *D_L=(a';b',c',d')* as explained above
time|Computation time of the  bundle cohomology
splits|The number of components the curve splits into
h0|The dimension of the zeroth cohomology group of the bundle on the curve
h1|The dimension of the first cohomology group of the bundle on the curve
SplitIntersections|Intersections of the line bundle with the split components of the curve
rho|Integer lower bound on the dimension of h0 computed using Brill-Noether theory
generic|Indicates whether the cohomology is generic, i.e. whether h0 and h1 have their minimal values (indicated by a 1) or not (indicated by a 0)
local-sections-A|The values of *[h0,h1]* for each split component of the curve. 'NA' means we have not computed the value individually

# Citation
If you want to cite this data, please use the bibtex below or download it [here]("./Bies2020.bib"):
```bibtex
@article{1804533,
    author = "Bies, Martin and Cveti{\v c}, Mirjam and Donagi, Ron and Lin, Ling and Liu, Muyang and Ruehle, Fabian",
    title = "{Machine Learning and Algebraic Approaches towards Complete Matter Spectra in 4d F-theory}",
    eprint = "2007.00009",
    archivePrefix = "arXiv",
    primaryClass = "hep-th",
    reportNumber = "UPR-1305-T, CERN-TH-2020-111",
    month = "6",
    year = "2020"
}
@Misc{Database,
  author       = {Bies, Martin and Cveti{\v c}, Mirjam and Donagi, Ron and Lin, Ling and Liu, Muyang and Rühle, Fabian},
  howpublished = {\url{https://github.com/Learning-line-bundle-cohomology/Database}},
  title        = {Database},
  year         = {2020},
}
```

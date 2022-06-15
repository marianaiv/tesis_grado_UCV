```{console}
>jb build tesis --builder pdflatex
Running Jupyter-Book v0.12.2
Source Folder: C:\Users\maria\OneDrive\Documents\Universe\University\01_UCV\Tesis\tesis_grado_UCV\tesis
Config Path: C:\Users\maria\OneDrive\Documents\Universe\University\01_UCV\Tesis\tesis_grado_UCV\tesis\_config.yml
Output Path: C:\Users\maria\OneDrive\Documents\Universe\University\01_UCV\Tesis\tesis_grado_UCV\tesis\_build\latex
Running Sphinx v4.5.0
loading translations [spanish]... done
[etoc] Changing master_doc to 'intro'
loading pickled environment... checking bibtex cache... up to date
done
WARNING: no Babel option known for language 'spanish'
myst v0.15.2: MdParserConfig(renderer='sphinx', commonmark_only=False, enable_extensions=['amsmath', 'colon_fence', 'dollarmath', 'linkify', 'substitution', 'tasklist'], dmath_allow_labels=True, dmath_allow_space=True, dmath_allow_digits=True, dmath_double_inline=False, update_mathjax=True, mathjax_classes='tex2jax_process|mathjax_process|math|output_area', disable_syntax=[], url_schemes=['mailto', 'http', 'https'], heading_anchors=None, heading_slug_func=None, html_meta=[], footnote_transition=True, substitutions=[], sub_delimiters=['{', '}'], words_per_minute=200)
sphinx-jupyterbook-latex v0.4.6:engine='xelatex', toplevel_section='chapter', imgconverter='sphinx.ext.imgconverter', show_tocs='list'
building [mo]: targets for 0 po files that are out of date
building [latex]: all documents
updating environment: 0 added, 2 changed, 0 removed
reading sources... [100%] capitulos/marco-teorico/resumen
looking for now-outdated files... none found
pickling environment... done
checking consistency... C:\Users\maria\OneDrive\Documents\Universe\University\01_UCV\Tesis\tesis_grado_UCV\tesis\README.md: WARNING: document isn't included in any toctree
done
processing python.tex... intro capitulos/marco-teorico/resumen capitulos/marco-teorico/modelo-estandar capitulos/marco-teorico/cromodinamica-cuantica capitulos/marco-teorico/reconstruccion-jets capitulos/marco-teorico/mas-alla-del-ms capitulos/marco-teorico/aprendizaje-automatico capitulos/marco-teorico/reproducibilidad capitulos/marco-teorico/olimpiadas-LHC capitulos/referencias/referencias 
resolving references...
WARNING: convert command 'magick' cannot be run, check the image_converter setting: [WinError 2] The system cannot find the file specified
done
writing... WARNING: no Babel option known for language 'spanish'
done
copying images... [100%] figuras/lhco-resultados.png
copying TeX support files... copying TeX support files...
done
build succeeded, 4 warnings.

The LaTeX files are in tesis\_build\latex.
Finished generating latex for book...
Converting book latex into PDF...
Win CP console initial and current in/out Win: (850, 850), (1252, 1252)
Coding system for system and terminal: 'CP1252'
---
Rc files read:
  latexmkrc
Latexmk: This is Latexmk, John Collins, 17 Mar. 2022. Version 4.77, version: 4.77.
Latexmk: applying rule 'pdflatex'...
Rule 'pdflatex': File changes, etc:
   Changed files, or newly in use since previous run(s):
  python.out
  python.tex
Rule 'pdflatex': The following rules & subrules became out-of-date:
  pdflatex
------------
Run number 1 of rule 'pdflatex'
------------
------------
Running 'xelatex    -recorder  "python.tex"'
------------
This is XeTeX, Version 3.141592653-2.6-0.999994 (TeX Live 2022) (preloaded format=xelatex)
 restricted \write18 enabled.
entering extended mode
(./python.tex
LaTeX2e <2021-11-15> patch level 1
L3 programming layer <2022-04-10> (./jupyterBook.cls
Document Class: jupyterBook 2020/11/06
(c:/texlive/2022/texmf-dist/tex/latex/xcolor/xcolor.sty
(c:/texlive/2022/texmf-dist/tex/latex/graphics-cfg/color.cfg)
(c:/texlive/2022/texmf-dist/tex/latex/graphics-def/xetex.def))
(c:/texlive/2022/texmf-dist/tex/latex/base/inputenc.sty

Package inputenc Warning: inputenc package ignored with utf8 based engines.

) (c:/texlive/2022/texmf-dist/tex/latex/graphics/graphicx.sty
(c:/texlive/2022/texmf-dist/tex/latex/graphics/keyval.sty)
(c:/texlive/2022/texmf-dist/tex/latex/graphics/graphics.sty
(c:/texlive/2022/texmf-dist/tex/latex/graphics/trig.sty)
(c:/texlive/2022/texmf-dist/tex/latex/graphics-cfg/graphics.cfg)))
(c:/texlive/2022/texmf-dist/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(c:/texlive/2022/texmf-dist/tex/latex/amsmath/amstext.sty
(c:/texlive/2022/texmf-dist/tex/latex/amsmath/amsgen.sty))
(c:/texlive/2022/texmf-dist/tex/latex/amsmath/amsbsy.sty)
(c:/texlive/2022/texmf-dist/tex/latex/amsmath/amsopn.sty))
(c:/texlive/2022/texmf-dist/tex/latex/amsfonts/amssymb.sty
(c:/texlive/2022/texmf-dist/tex/latex/amsfonts/amsfonts.sty))
(c:/texlive/2022/texmf-dist/tex/latex/amsmath/amscd.sty)
(c:/texlive/2022/texmf-dist/tex/latex/jknapltx/mathrsfs.sty)
(c:/texlive/2022/texmf-dist/tex/latex/pgf/frontendlayer/tikz.sty
(c:/texlive/2022/texmf-dist/tex/latex/pgf/basiclayer/pgf.sty
(c:/texlive/2022/texmf-dist/tex/latex/pgf/utilities/pgfrcs.sty
(c:/texlive/2022/texmf-dist/tex/generic/pgf/utilities/pgfutil-common.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/utilities/pgfutil-common-lists.tex)
) (c:/texlive/2022/texmf-dist/tex/generic/pgf/utilities/pgfutil-latex.def)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/utilities/pgfrcs.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/pgf.revision.tex)))
(c:/texlive/2022/texmf-dist/tex/latex/pgf/basiclayer/pgfcore.sty
(c:/texlive/2022/texmf-dist/tex/latex/pgf/systemlayer/pgfsys.sty
(c:/texlive/2022/texmf-dist/tex/generic/pgf/systemlayer/pgfsys.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/utilities/pgfkeys.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/utilities/pgfkeysfiltered.code.tex)
) (c:/texlive/2022/texmf-dist/tex/generic/pgf/systemlayer/pgf.cfg)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/systemlayer/pgfsys-xetex.def
(c:/texlive/2022/texmf-dist/tex/generic/pgf/systemlayer/pgfsys-dvipdfmx.def
(c:/texlive/2022/texmf-dist/tex/generic/pgf/systemlayer/pgfsys-common-pdf.def))
))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/systemlayer/pgfsyssoftpath.code.tex
)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/systemlayer/pgfsysprotocol.code.tex
)) (c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcore.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmath.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathcalc.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathutil.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathparser.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.basic.code.te
x)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.trigonometric
.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.random.code.t
ex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.comparison.co
de.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.base.code.tex
)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.round.code.te
x)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.misc.code.tex
)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfunctions.integerarithm
etics.code.tex)))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmathfloat.code.tex))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfint.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorepoints.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorepathconstruct.cod
e.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorepathusage.code.te
x)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorescopes.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcoregraphicstate.code
.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcoretransformations.c
ode.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorequick.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcoreobjects.code.tex)

(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorepathprocessing.co
de.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorearrows.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcoreshade.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcoreimage.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcoreexternal.code.tex
))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorelayers.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcoretransparency.code
.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorepatterns.code.tex
) (c:/texlive/2022/texmf-dist/tex/generic/pgf/basiclayer/pgfcorerdf.code.tex)))
 (c:/texlive/2022/texmf-dist/tex/generic/pgf/modules/pgfmoduleshapes.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/modules/pgfmoduleplot.code.tex)
(c:/texlive/2022/texmf-dist/tex/latex/pgf/compatibility/pgfcomp-version-0-65.st
y)
(c:/texlive/2022/texmf-dist/tex/latex/pgf/compatibility/pgfcomp-version-1-18.st
y)) (c:/texlive/2022/texmf-dist/tex/latex/pgf/utilities/pgffor.sty
(c:/texlive/2022/texmf-dist/tex/latex/pgf/utilities/pgfkeys.sty
(c:/texlive/2022/texmf-dist/tex/generic/pgf/utilities/pgfkeys.code.tex))
(c:/texlive/2022/texmf-dist/tex/latex/pgf/math/pgfmath.sty
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmath.code.tex))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/utilities/pgffor.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/math/pgfmath.code.tex)))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/tikz.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/libraries/pgflibraryplothandlers.co
de.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/modules/pgfmodulematrix.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzli
brarytopaths.code.tex)))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzli
braryarrows.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/libraries/pgflibraryarrows.code.tex
))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzli
brarycalc.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzli
braryintersections.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/libraries/pgflibraryintersections.c
ode.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/libraries/pgflibraryfpu.code.tex)))

(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzli
brarydecorations.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/modules/pgfmoduledecorations.code.t
ex)) (c:/texlive/2022/texmf-dist/tex/latex/pgfplots/pgfplots.sty
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplots.revision.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplots.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplotscore.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/sys/pgfplotssysgeneric.code.te
x))
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/libs/pgfplotslibrary.code.tex)

(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/oldpgfcompatib/pgfplotsoldpgfs
upp_loader.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/util/pgfplotsutil.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/liststructure/pgfplotsliststru
cture.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/liststructure/pgfplotsliststru
ctureext.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/liststructure/pgfplotsarray.co
de.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/liststructure/pgfplotsmatrix.c
ode.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/numtable/pgfplotstableshared.c
ode.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/liststructure/pgfplotsdeque.co
de.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/util/pgfplotsbinary.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/util/pgfplotsbinary.data.code.
tex))
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/util/pgfplotsutil.verb.code.te
x)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/libs/pgflibrarypgfplots.surfsh
ading.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/sys/pgflibrarypgfplots.surfsha
ding.pgfsys-xetex.def
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/sys/pgflibrarypgfplots.surfsha
ding.pgfsys-dvipdfmx.def))))
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/util/pgfplotscolormap.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/util/pgfplotscolor.code.tex))
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplotsstackedplots.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplotsplothandlers.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplotsmeshplothandler.code.t
ex
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplotsmeshplotimage.code.tex
))) (c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplots.scaling.code.tex)

(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplotscoordprocessing.code.t
ex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplots.errorbars.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplots.markers.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplotsticks.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/pgfplots.paths.code.tex)
(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzli
brarydecorations.pathmorphing.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/libraries/decorations/pgflibrarydec
orations.pathmorphing.code.tex))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzli
brarydecorations.pathreplacing.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/libraries/decorations/pgflibrarydec
orations.pathreplacing.code.tex))
(c:/texlive/2022/texmf-dist/tex/generic/pgfplots/libs/tikzlibrarypgfplots.conto
urlua.code.tex))
(c:/texlive/2022/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzli
braryplotmarks.code.tex
(c:/texlive/2022/texmf-dist/tex/generic/pgf/libraries/pgflibraryplotmarks.code.
tex))) (c:/texlive/2022/texmf-dist/tex/latex/bbm-macros/bbm.sty)
(./sphinxmanual.cls
Document Class: sphinxmanual 2019/12/01 v2.3.0 Document class (Sphinx manual)
(c:/texlive/2022/texmf-dist/tex/latex/base/report.cls
Document Class: report 2021/10/04 v1.4n Standard LaTeX document class
(c:/texlive/2022/texmf-dist/tex/latex/base/size10.clo)))
(c:/texlive/2022/texmf-dist/tex/latex/changepage/changepage.sty))
(c:/texlive/2022/texmf-dist/tex/latex/cmap/cmap.sty

Package cmap Warning: pdftex not detected - exiting.

) (c:/texlive/2022/texmf-dist/tex/latex/fontspec/fontspec.sty
(c:/texlive/2022/texmf-dist/tex/latex/l3packages/xparse/xparse.sty
(c:/texlive/2022/texmf-dist/tex/latex/l3kernel/expl3.sty
(c:/texlive/2022/texmf-dist/tex/latex/l3backend/l3backend-xetex.def)))
(c:/texlive/2022/texmf-dist/tex/latex/fontspec/fontspec-xetex.sty
(c:/texlive/2022/texmf-dist/tex/latex/base/fontenc.sty)
(c:/texlive/2022/texmf-dist/tex/latex/fontspec/fontspec.cfg)))
(c:/texlive/2022/texmf-dist/tex/latex/polyglossia/polyglossia.sty
(c:/texlive/2022/texmf-dist/tex/latex/etoolbox/etoolbox.sty)
(c:/texlive/2022/texmf-dist/tex/latex/makecmds/makecmds.sty)
(c:/texlive/2022/texmf-dist/tex/latex/xkeyval/xkeyval.sty
(c:/texlive/2022/texmf-dist/tex/generic/xkeyval/xkeyval.tex
(c:/texlive/2022/texmf-dist/tex/generic/xkeyval/xkvutils.tex)))
(c:/texlive/2022/texmf-dist/tex/generic/iftex/iftex.sty)
(c:/texlive/2022/texmf-dist/tex/latex/l3packages/l3keys2e/l3keys2e.sty)
(c:/texlive/2022/texmf-dist/tex/latex/polyglossia/gloss-latex.lde))
(c:/texlive/2022/texmf-dist/tex/latex/polyglossia/gloss-english.ldf)
(c:/texlive/2022/texmf-dist/tex/latex/fncychap/fncychap.sty) (./sphinx.sty
(c:/texlive/2022/texmf-dist/tex/generic/ltxcmds/ltxcmds.sty)
(c:/texlive/2022/texmf-dist/tex/latex/kvoptions/kvoptions.sty
(c:/texlive/2022/texmf-dist/tex/generic/kvsetkeys/kvsetkeys.sty))
(./sphinxoptionshyperref.sty) (./sphinxoptionsgeometry.sty)
(c:/texlive/2022/texmf-dist/tex/latex/base/textcomp.sty)
(c:/texlive/2022/texmf-dist/tex/latex/float/float.sty)
(c:/texlive/2022/texmf-dist/tex/latex/wrapfig/wrapfig.sty)
(c:/texlive/2022/texmf-dist/tex/latex/capt-of/capt-of.sty)
(c:/texlive/2022/texmf-dist/tex/latex/tools/multicol.sty)
(./sphinxlatexgraphics.sty) (./sphinxlatexadmonitions.sty
(c:/texlive/2022/texmf-dist/tex/latex/framed/framed.sty))
(./sphinxlatexliterals.sty
(c:/texlive/2022/texmf-dist/tex/latex/fancyvrb/fancyvrb.sty)
(c:/texlive/2022/texmf-dist/tex/latex/base/alltt.sty)
(c:/texlive/2022/texmf-dist/tex/latex/upquote/upquote.sty)
(c:/texlive/2022/texmf-dist/tex/latex/needspace/needspace.sty))
(./sphinxlatexshadowbox.sty) (./sphinxlatexcontainers.sty)
(./sphinxhighlight.sty) (./sphinxlatextables.sty
(c:/texlive/2022/texmf-dist/tex/latex/tabulary/tabulary.sty
(c:/texlive/2022/texmf-dist/tex/latex/tools/array.sty))
(c:/texlive/2022/texmf-dist/tex/latex/tools/longtable.sty)
(c:/texlive/2022/texmf-dist/tex/latex/varwidth/varwidth.sty))
(./sphinxlatexnumfig.sty) (./sphinxlatexlists.sty) (./sphinxpackagefootnote.sty
) (./sphinxlatexindbibtoc.sty
(c:/texlive/2022/texmf-dist/tex/latex/base/makeidx.sty))
(./sphinxlatexstylepage.sty
(c:/texlive/2022/texmf-dist/tex/latex/parskip/parskip.sty
(c:/texlive/2022/texmf-dist/tex/latex/parskip/parskip-2001-04-09.sty))
(c:/texlive/2022/texmf-dist/tex/latex/fancyhdr/fancyhdr.sty))
(./sphinxlatexstyleheadings.sty
(c:/texlive/2022/texmf-dist/tex/latex/titlesec/titlesec.sty))
(./sphinxlatexstyletext.sty) (./sphinxlatexobjects.sty))
(c:/texlive/2022/texmf-dist/tex/latex/geometry/geometry.sty
(c:/texlive/2022/texmf-dist/tex/generic/iftex/ifvtex.sty))
(c:/texlive/2022/texmf-dist/tex/latex/hyperref/hyperref.sty
(c:/texlive/2022/texmf-dist/tex/generic/pdftexcmds/pdftexcmds.sty
(c:/texlive/2022/texmf-dist/tex/generic/infwarerr/infwarerr.sty))
(c:/texlive/2022/texmf-dist/tex/generic/kvdefinekeys/kvdefinekeys.sty)
(c:/texlive/2022/texmf-dist/tex/generic/pdfescape/pdfescape.sty)
(c:/texlive/2022/texmf-dist/tex/latex/hycolor/hycolor.sty)
(c:/texlive/2022/texmf-dist/tex/latex/letltxmacro/letltxmacro.sty)
(c:/texlive/2022/texmf-dist/tex/latex/auxhook/auxhook.sty)
(c:/texlive/2022/texmf-dist/tex/latex/hyperref/pd1enc.def)
(c:/texlive/2022/texmf-dist/tex/generic/intcalc/intcalc.sty)
(c:/texlive/2022/texmf-dist/tex/generic/etexcmds/etexcmds.sty)
(c:/texlive/2022/texmf-dist/tex/latex/hyperref/puenc.def)
(c:/texlive/2022/texmf-dist/tex/latex/url/url.sty)
(c:/texlive/2022/texmf-dist/tex/generic/bitset/bitset.sty
(c:/texlive/2022/texmf-dist/tex/generic/bigintcalc/bigintcalc.sty))
(c:/texlive/2022/texmf-dist/tex/latex/base/atbegshi-ltx.sty))
(c:/texlive/2022/texmf-dist/tex/latex/hyperref/hxetex.def
(c:/texlive/2022/texmf-dist/tex/generic/stringenc/stringenc.sty)
(c:/texlive/2022/texmf-dist/tex/latex/rerunfilecheck/rerunfilecheck.sty
(c:/texlive/2022/texmf-dist/tex/latex/base/atveryend-ltx.sty)
(c:/texlive/2022/texmf-dist/tex/generic/uniquecounter/uniquecounter.sty)))
(c:/texlive/2022/texmf-dist/tex/latex/oberdiek/hypcap.sty)
(./sphinxmessages.sty)
(c:/texlive/2022/texmf-dist/tex/xelatex/ucharclasses/ucharclasses.sty
(c:/texlive/2022/texmf-dist/tex/generic/iftex/ifxetex.sty))
(c:/texlive/2022/texmf-dist/tex/latex/unicode-math/unicode-math.sty
(c:/texlive/2022/texmf-dist/tex/latex/unicode-math/unicode-math-xetex.sty
(c:/texlive/2022/texmf-dist/tex/latex/base/fix-cm.sty
(c:/texlive/2022/texmf-dist/tex/latex/base/ts1enc.def))
(c:/texlive/2022/texmf-dist/tex/latex/unicode-math/unicode-math-table.tex)))
(c:/texlive/2022/texmf-dist/tex/latex/hyperref/puenc-greekbasic.def)
(c:/texlive/2022/texmf-dist/tex/latex/hyperref/psdextra.def)
Writing index file python.idx
(./python.aux)

Package pgfplots Warning: running in backwards compatibility mode (unsuitable t
ick labels; missing features). Consider writing \pgfplotsset{compat=1.18} into 
your preamble.
 on input line 95.

*geometry* driver: auto-detecting
*geometry* detected driver: xetex
(c:/texlive/2022/texmf-dist/tex/latex/hyperref/nameref.sty
(c:/texlive/2022/texmf-dist/tex/latex/refcount/refcount.sty)
(c:/texlive/2022/texmf-dist/tex/generic/gettitlestring/gettitlestring.sty))
(./python.out) (./python.out)
(c:/texlive/2022/texmf-dist/tex/generic/stringenc/se-ascii-print.def)
(c:/texlive/2022/texmf-dist/tex/latex/amsfonts/umsa.fd)
(c:/texlive/2022/texmf-dist/tex/latex/amsfonts/umsb.fd)
(c:/texlive/2022/texmf-dist/tex/latex/jknapltx/ursfs.fd) [1] [2] (./python.toc)
[1] [2]
Underfull \hbox (badness 10000) in paragraph at lines 197--197
[]\TU/FreeSerif(0)/m/n/10 Reina Camacho

Overfull \hbox (2.90416pt too wide) in paragraph at lines 197--197
[][][]\TU/FreeSerif(0)/m/n/10 reina.camacho@cern.ch[][]| 

Underfull \hbox (badness 10000) in paragraph at lines 197--197
[][][]\TU/FreeSerif(0)/m/n/10 @camachor-

Underfull \hbox (badness 10000) in paragraph at lines 197--197
[]\TU/FreeSerif(0)/m/n/10 Camila Rangel

Underfull \hbox (badness 10000) in paragraph at lines 197--197
[][][]\TU/FreeSerif(0)/m/n/10 crangel-

Underfull \hbox (badness 10000) in paragraph at lines 197--197
[][][]\TU/FreeSerif(0)/m/n/10 @crangel-

Package fancyhdr Warning: \headheight is too small (12.0pt): 
(fancyhdr)                Make it at least 23.17004pt, for example:
(fancyhdr)                \setlength{\headheight}{23.17004pt}.
(fancyhdr)                You might also make \topmargin smaller to compensate:

(fancyhdr)                \addtolength{\topmargin}{-11.17004pt}.

[1]

Package fancyhdr Warning: \headheight is too small (12.0pt):
(fancyhdr)                Make it at least 23.17004pt, for example:
(fancyhdr)                \setlength{\headheight}{23.17004pt}.
(fancyhdr)                You might also make \topmargin smaller to compensate:

(fancyhdr)                \addtolength{\topmargin}{-11.17004pt}.

[2]
Chapter 1.

LaTeX Warning: Hyper reference `capitulos/marco-teorico/reconstruccion-jets:jet
s' on page 3 undefined on input line 210.


LaTeX Warning: Reference `capitulos/marco-teorico/reconstruccion-jets:jets' on
page 3 undefined on input line 210.


LaTeX Warning: Hyper reference `capitulos/marco-teorico/mas-alla-del-ms:bsm' on
 page 3 undefined on input line 210.


LaTeX Warning: Reference `capitulos/marco-teorico/mas-alla-del-ms:bsm' on page
3 undefined on input line 210.


LaTeX Warning: Hyper reference `capitulos/marco-teorico/aprendizaje-automatico:
ml' on page 3 undefined on input line 210.


LaTeX Warning: Reference `capitulos/marco-teorico/aprendizaje-automatico:ml' on
 page 3 undefined on input line 210.


LaTeX Warning: Hyper reference `capitulos/marco-teorico/reproducibilidad:rpd' o
n page 3 undefined on input line 210.


LaTeX Warning: Reference `capitulos/marco-teorico/reproducibilidad:rpd' on page
 3 undefined on input line 210.

[3]

Package fancyhdr Warning: \headheight is too small (12.0pt):
(fancyhdr)                Make it at least 23.17004pt, for example:
(fancyhdr)                \setlength{\headheight}{23.17004pt}.
(fancyhdr)                You might also make \topmargin smaller to compensate:

(fancyhdr)                \addtolength{\topmargin}{-11.17004pt}.

[4]

Package fancyhdr Warning: \headheight is too small (12.0pt):
(fancyhdr)                Make it at least 23.17004pt, for example:
(fancyhdr)                \setlength{\headheight}{23.17004pt}.
(fancyhdr)                You might also make \topmargin smaller to compensate:

(fancyhdr)                \addtolength{\topmargin}{-11.17004pt}.

[5]
! Argument of \Hy@tempa has an extra }.
<inserted text>
                \par
l.312 ...os/referencias/referencias:id14}{12}{]}.}
                                                  \label{\detokenize{capitul...

? del .git\index.lock
Type <return> to proceed, S to scroll future error messages,
R to run without stopping, Q to run quietly,
I to insert something, E to edit your file,
1 or ... or 9 to ignore the next 1 to 9 tokens of input,
H for help, X to quit.
?
Runaway argument?
\@captype {\hyper@link@ }\def \reserved@b {\hyper@link@ [link]}\futurelet \ETC.
! Paragraph ended before \Hy@tempa was complete.
<to be read again>
                   \par 
l.312 ...os/referencias/referencias:id14}{12}{]}.}
                                                  \label{\detokenize{capitul...

?
! Argument of \Hy@tempa has an extra }.
<inserted text>
                \par
l.319 ...os/referencias/referencias:id14}{12}{]}.}
                                                  \label{\detokenize{capitul...

?
Runaway argument?
\@captype {\hyper@link@ }\def \reserved@b {\hyper@link@ [link]}\futurelet \ETC.
! Paragraph ended before \Hy@tempa was complete.
<to be read again>
                   \par
l.319 ...os/referencias/referencias:id14}{12}{]}.}
                                                  \label{\detokenize{capitul...

?

Package fancyhdr Warning: \headheight is too small (12.0pt): 
(fancyhdr)                Make it at least 23.17004pt, for example:
(fancyhdr)                \setlength{\headheight}{23.17004pt}.
(fancyhdr)                You might also make \topmargin smaller to compensate:

(fancyhdr)                \addtolength{\topmargin}{-11.17004pt}.

[6]

Package fancyhdr Warning: \headheight is too small (12.0pt):
(fancyhdr)                Make it at least 23.17004pt, for example:
(fancyhdr)                \setlength{\headheight}{23.17004pt}.
(fancyhdr)                You might also make \topmargin smaller to compensate:

(fancyhdr)                \addtolength{\topmargin}{-11.17004pt}.

[7]
! Argument of \Hy@tempa has an extra }.
<inserted text>
                \par 
l.338 ...os/referencias/referencias:id16}{14}{]}.}
                                                  \label{\detokenize{capitul...

?
Runaway argument?
\@captype {\hyper@link@ }\def \reserved@b {\hyper@link@ [link]}\futurelet \ETC.
! Paragraph ended before \Hy@tempa was complete.
<to be read again>
                   \par 
l.338 ...os/referencias/referencias:id16}{14}{]}.}
                                                  \label{\detokenize{capitul...

?

Package fancyhdr Warning: \headheight is too small (12.0pt): 
(fancyhdr)                Make it at least 23.17004pt, for example:
(fancyhdr)                \setlength{\headheight}{23.17004pt}.
(fancyhdr)                You might also make \topmargin smaller to compensate:

(fancyhdr)                \addtolength{\topmargin}{-11.17004pt}.

[8]

LaTeX Warning: Hyper reference `capitulos/marco-teorico/reconstruccion-jets:jet
s-desarrollo' on page 9 undefined on input line 364.


LaTeX Warning: Reference `capitulos/marco-teorico/reconstruccion-jets:jets-desa
rrollo' on page 9 undefined on input line 364.


LaTeX Warning: Hyper reference `capitulos/marco-teorico/reconstruccion-jets:jet
s-qcd' on page 9 undefined on input line 367.


LaTeX Warning: Reference `capitulos/marco-teorico/reconstruccion-jets:jets-qcd'
 on page 9 undefined on input line 367.

! TeX capacity exceeded, sorry [input stack size=10000].
<to be read again>
                   \if@capstart
l.380 ...romodinamica-cuantica:qcd-gluongluon}}})}
                                                  \label{\detokenize{capitul...

Output written on python.pdf (12 pages).
Transcript written on python.log.
Latexmk: Getting log file 'python.log'
Latexmk: Examining 'python.fls'
PWD line not in UTF-8
Latexmk: Examining 'python.log'
Latexmk: Index file 'python.idx' was written
Latexmk: Log file says output to 'python.pdf'
Latexmk: Summary of warnings from last run of *latex:
  Latex failed to resolve 6 reference(s)
Latexmk: ====List of undefined refs and citations:
  Reference `capitulos/marco-teorico/reconstruccion-jets:jets' on page 3 undefined on input line 210
  Reference `capitulos/marco-teorico/mas-alla-del-ms:bsm' on page 3 undefined on input line 210
  Reference `capitulos/marco-teorico/aprendizaje-automatico:ml' on page 3 undefined on input line 210
  Reference `capitulos/marco-teorico/reproducibilidad:rpd' on page 3 undefined on input line 210
  Reference `capitulos/marco-teorico/reconstruccion-jets:jets-desarrollo' on page 9 undefined on input line 364
  Reference `capitulos/marco-teorico/reconstruccion-jets:jets-qcd' on page 9 undefined on input line 367
Latexmk: Errors, so I did not complete making targets
Collected error summary (may duplicate other messages):
  pdflatex: Command for 'pdflatex' gave return code 1
      Refer to 'python.log' for details
Latexmk: If appropriate, the -f option can be used to get latexmk
  to try to force complete processing.
Reverting Windows console CPs to (in,out) = (850,850)
C:\texlive\2022\bin\win32\runscript.tlu:915: command failed with exit code 12:
perl.exe c:\texlive\2022\texmf-dist\scripts\latexmk\latexmk.pl -pdf -dvi- -ps-  python.tex

===============================================================================

A PDF of your book can be found at:
```
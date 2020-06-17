diagnosis:
	$s specificationFileName=TEILex0-ODD.xml -xsl:ODD-Diagnosis.xsl TEILex0-ODD.xml > TEILex0-ODD.html

# Have to have local source of p5subset, as my Java is too old to fetch it with https!
PARAMS = --localsource=p5subset.xml TEILex0-ODD.xml
schema:
	Stylesheets/bin/teitorelaxng    ${PARAMS} out/TEILex0.rng
	Stylesheets/bin/teitornc        ${PARAMS} out/TEILex0.rnc
	Stylesheets/bin/teitodtd        ${PARAMS} out/TEILex0.dtd
	## Stylesheets/bin/teitoxsd        ${PARAMS} out/TEILex0.xsd
	Stylesheets/bin/teitoschematron ${PARAMS} out/TEILex0.sch

H = ...
html:	val-odd
	Stylesheets/bin/teitohtml --profiledir=$H --profile=profile --odd ${PARAMS} ../docs/index.html

# ODD does *not* validate!
val-odd:
	$j tei_odds.rng TEILex0-ODD.xml

j = java -jar /usr/local/bin/jing.jar
#s = java -jar ~/bin/saxon9he.jar
#s = java -jar /usr/local/bin/saxon9he.jar
s = java -Djavax.xml.parsers.DocumentBuilderFactory=org.apache.xerces.jaxp.DocumentBuilderFactoryImpl -Djavax.xml.parsers.SAXParserFactory=org.apache.xerces.jaxp.SAXParserFactoryImpl net.sf.saxon.Transform

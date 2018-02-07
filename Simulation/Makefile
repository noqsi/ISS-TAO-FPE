GNET=gnetlist -g spice-noqsi
NGSPICE=ngspice

%.cir : %.sch
	$(GNET) $< -o $@

S2PS=gschem -p -o $@ -s ../Schematic/print.scm $<

%.sym.ps : %.sym
	$(S2PS)

%.ps : %.sch
	$(S2PS)

PS2PDF=ps2pdf -sPAPERSIZE=letter

%.pdf : %.ps
	$(PS2PDF) $<


SerialTest : SerialTest.cir OneDriver.cir 3phase.cir Ad8005.cir \
	MMBT2222A.mod MMBT2907A.mod
	$(NGSPICE) $^

SerialBoost : SerialBoost.cir 3phase.cir \
	MMBT2222A.mod MMBT2907A.mod
	$(NGSPICE) $^

clean :
	rm -f *~ \#* SerialTest.cir OneDriver.cir 3phase.cir SerialBoost.cir

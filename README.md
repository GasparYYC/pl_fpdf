# pl_fpdf

Pl_fpdf is a pl/sql package that provides functions and procedure to produce pdf files from Oracle database.

This code gives you the same functions than FPDF, except that it converts all the images you need in PNG.
PHP library FPDF which was written by Olivier Plathey. (http://www.fpdf.org/)

Required Environment
```
- Oracle en version 10g (10.2.0.1 and above).
- Installation ofOracle Web Tool Kit required (owa, htp and htf packages).
- OrdSys.OrdImage required (Oracle cartridge for images).
- Installation of package URIFactory required.
```

Sample codes
helloWord : Note that the "output" procedure calls automatically "ClosePdf".
```SQL
procedure helloworld is
begin
        pdf.FPDF('P','cm','A4');
        pdf.openpdf;
        pdf.AddPage();
        pdf.SetFont('Arial','B',16);
        pdf.Cell(0,1.2,'Hello World',0,1,'C');
      pdf.Output();
end helloworld;
```

Put an image in a pdf file:
```SQL
procedure testImg is
 img varchar2(2000);
begin
        pdf.FPDF('P','cm','A4');
        pdf.openpdf;
        pdf.AddPage();
        pdf.SetFont('Arial','B',16);
      img := 'http://www.laclasse.com/v25/images/logo-laclasse.gif';
      pdf.Image(img,1, 1, 10);
      pdf.Output();
end testImg;
```

Note that it uses the ORDImage data type to place images in PDF documents, so if you are running Oracle XE (which doesn't include the ORDImage data type), you need to comment out the few procedures that deal with this data type (and obviously you will not be able to include images in your PDF documents...).

PANDOC = pandoc -s -S 
HTM  = home.htm message1.htm message2.htm message3.htm people1.htm people2.htm video1.htm article1.htm article2.htm article3.htm article4.htm info.htm
MD   = message.md message1.md  message2.md  message3.md  people.md people1.md  people2.md video.md video1.md article.md article1.md article2.md article3.md article4.md info.md
HFLAGS = -c ../css/pmag.css -B header.htm -A footer.htm 
RM = rm -f
EOPT = --margin-top=16 --margin-bottom=16 --margin-left=20 --margin-right=20 --base-font-size=9 --font-size-mapping="7, 8, 9, 12, 14, 16, 20, 24"

.PHONY: all clean

all: htm ipad3 A4 shtm mobi 

A5: 
	ebook-convert ../book/pmag201302.epub ../book/pmag201302A5.pdf $(EOPT) --custom-size=8x6

A4: 
	ebook-convert ../book/pmag201302A4.epub ../book/pmag201302A4.pdf $(EOPT)
	
epubA4:
	$(PANDOC) -S --toc --epub-metadata=metadata.xml --epub-stylesheet=../css/pmag.css --epub-cover-image=../img/pmag_cover_A4.png toc.md $(MD) -o ../book/pmag201302A4.epub

epub:
	$(PANDOC) -S --toc --epub-metadata=metadata.xml --epub-stylesheet=../css/pmag.css --epub-cover-image=../img/pmag_cover.jpg toc.md $(MD) -o ../book/pmag201302.epub

ipad3:
	ebook-convert ../book/pmag201302.epub ../book/pmag201302ipad3.pdf $(EOPT) --output-profile=ipad3

mobi: epub
	ebook-convert ../book/pmag201302.epub ../book/pmag201302ipad3.mobi $(EOPT) --output-profile=ipad3
	
tex:
	$(PANDOC) --chapters --template=A4.tex -S --toc $(MD) -o pmag201302A4.tex

xml: 
	$(PANDOC) --chapters -w opendocument -S --toc $(MD) -o ../book/pmag201302A4.xml
	
htm: $(HTM)

shtm: 
	$(PANDOC) --toc $(MD) -o ../book/pmag201302.htm $(HFLAGS)

%.htm: %.md
	$(PANDOC) $< -o ../htm/$@ $(HFLAGS)
	
clean: 
	${RM} ../htm/*.*

#	$(PANDOC) --chapters --variable fontsize=12pt --template=A5.tex -S --toc $(MD) -o ../book/pmag201302A5.pdf
#	$(PANDOC) --chapters --variable fontsize=12pt --template=A4.tex -S --toc $(MD) -o ../book/pmag201302A4.pdf
#	$(PANDOC) --chapters -S --toc --epub-metadata=metadata.xml --epub-stylesheet=../css/pmag.css --epub-cover-image=../img/pmag_cover.png $(MD) -o ../book/pmag201302.epub
# odt: epub
#	ebook-convert ../book/pmag201302.epub ../book/pmag201302ipad3.odt $(EOPT) --output-profile=ipad3
#	$(PANDOC) --chapters -S --toc $(MD) -o ../book/pmag201302A4.odt
# MD   = preface.md message.md message1.md  message2.md  message3.md  people.md people1.md  people2.md  video.md video1.md  info.md tail.md // for pandoc pdf append tail
# EOPT1 = --output-profile=ipad3 --extra-css=../css/pmag.css --margin-top=16 --margin-bottom=16 --margin-left=20 --margin-right=20 --base-font-size=10 --disable-font-rescaling  --font-size-mapping="7, 8, 10, 12, 14, 16, 20, 24"

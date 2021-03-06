################## BASE IMAGE ######################
FROM biocontainers/bamtools:latest

################## METADATA ######################
LABEL base.image="bamtools:latest"
LABEL version="3"
LABEL software="TPMCalculator"
LABEL software.version="0.0.1"
LABEL description="This program calculates the TPM (Transcript per Millions) values for the exons and introns from NGS RNA-Seq aligned reads (BAM files)"
LABEL website="https://github.com/r78v10a07/TPMCalculator"
LABEL documentation="https://github.com/r78v10a07/TPMCalculator"
LABEL license="http://www.gnu.org/licenses/"
LABEL tags="RNA-seq"

################## MAINTAINER ######################
MAINTAINER Roberto Vera Alvarez <r78v10a07@gmail.com>

USER biodocker

ENV URL=https://github.com/r78v10a07/TPMCalculator
ENV FOLDER=TPMCalculator
ENV DST=/tmp
ENV BAMTOOLS_DIR=/home/biodocker
ENV CPPFLAGS="-I $BAMTOOLS_DIR/include/bamtools"
ENV LDFLAGS="-L $BAMTOOLS_DIR/lib/bamtools -Wl,-rpath,$BAMTOOLS_DIR/lib/bamtools"

RUN cd $DST && \
	git clone $URL && \
	cd $FOLDER && \
	make && \
	mv $DST/$FOLDER/bin/* /home/biodocker/bin/ && \
	rm -rf $DST/$FOLDER

WORKDIR /data/

CMD ["TPMCalculator"]

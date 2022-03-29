FROM public.ecr.aws/lambda/python:3.9

#dependencias da LIB libvips
RUN yum groupinstall -y "Development Tools"
RUN yum -y gtk-doc \
    libxml2-devel \
    libjpeg-turbo-devel \
    libpng-devel \
    libtiff-devel \
    libexif-devel \
    libgsf-devel \
    lcms-devel \
    ImageMagick-devel \
    gobject-introspection-devel \
    libwebp-devel \
    curl \
    && yum clean all

RUN install_libvips_from_source "--prefix=/usr"

COPY app.py requirements.txt ./

RUN /var/lang/bin/python3.9 -m pip install --upgrade pip

RUN python3.9 -m pip install -r requirements.txt -t .

# Command can be overwritten by providing a different command in the template directly.
CMD ["app.lambda_handler"]

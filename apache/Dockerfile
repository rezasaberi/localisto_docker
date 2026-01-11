FROM httpd:2.4-alpine

# Install dependencies if needed (e.g. for healthcheck)
RUN apk add --no-cache curl

# Enable necessary modules in httpd.conf
RUN sed -i \
    -e 's/^#\(LoadModule proxy_module modules\/mod_proxy.so\)/\1/' \
    -e 's/^#\(LoadModule proxy_fcgi_module modules\/mod_proxy_fcgi.so\)/\1/' \
    -e 's/^#\(LoadModule rewrite_module modules\/mod_rewrite.so\)/\1/' \
    -e 's/^#\(LoadModule negotiation_module modules\/mod_negotiation.so\)/\1/' \
    -e 's/^#\(LoadModule deflate_module modules\/mod_deflate.so\)/\1/' \
    conf/httpd.conf

# Include our custom config
COPY apache/shopshop.conf /usr/local/apache2/conf/extra/shopshop.conf
RUN echo "Include conf/extra/shopshop.conf" >> conf/httpd.conf

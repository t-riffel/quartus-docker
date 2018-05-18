FROM quartus-base:0.1
MAINTAINER Todd Riffel <todd.e.riffel@gmail.com>

USER root

# Web download
ADD http://download.altera.com/akdlm/software/acdsinst/17.1std/590/ib_installers/QuartusLiteSetup-17.1.0.590-linux.run /tmp/
ADD http://download.altera.com/akdlm/software/acdsinst/17.1std/590/ib_installers/cyclonev-17.1.0.590.qdz /tmp/
#ADD http://download.altera.com/akdlm/software/acdsinst/17.1std.1/593/update/QuartusSetup-17.1.1.593-linux.run /tmp/

# Fix file permissions
RUN cd /tmp/ && \
    chmod +x *.run && \
    chmod +r *

# Install Quartus
USER builder
RUN cd /tmp/ && \
    ./QuartusLiteSetup-17.1.0.590-linux.run --mode unattended --accept_eula 1
#RUN ./QuartusSetup-17.1.1.593-linux.run --mode unattended --accept_eula 1

# Add Quartus bin directorys to the path
ENV PATH $PATH:/home/builder/intelFPGA_lite/17.1/quartus/bin

# Cleanup to save space
USER root
RUN rm -rf /tmp/* /home/builder/intelFPGA/16.1/uninstall && \
    apt-get clean

USER builder


# Just the command line, but once you've built it, you can open the project in the GUI if you want to do things like look at the floorplan.
#
# EDIT: running the container with "-v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY" gets enough X11 to run the GUI.

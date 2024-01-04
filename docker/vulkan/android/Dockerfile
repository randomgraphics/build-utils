ARG base
FROM ${base}
LABEL description="Android Studio 2023.1.1.27 with Android SDK 31 and NDK 25.2.9519653"
ARG DEBIAN_FRONTEND=noninteractive

# Download and install wget
RUN apt-get update && apt-get install -y --no-install-recommends wget

# Download and install Android Studio
RUN mkdir /android/
RUN wget --no-check-certificate -q -c -O /android/studio.tar.gz https://redirector.gvt1.com/edgedl/android/studio/ide-zips/2023.1.1.27/android-studio-2023.1.1.27-linux.tar.gz
RUN cd /android;tar xzf studio.tar.gz;rm studio.tar.gz;mv android-studio studio

# Download and install command line tools
RUN apt-get update;apt-get install unzip
RUN wget --no-check-certificate -q -c -O /android/commandline-tools.zip https://dl.google.com/android/repository/commandlinetools-linux-10406996_latest.zip
RUN cd /android;unzip commandline-tools.zip;mkdir -p sdk/cmdline-tools;mv cmdline-tools sdk/cmdline-tools/latest;rm commandline-tools.zip

# Download Android SDK components
ARG JAVA_HOME=/android/studio/jbr
RUN yes|/android/sdk/cmdline-tools/latest/bin/sdkmanager --licenses
RUN /android/sdk/cmdline-tools/latest/bin/sdkmanager --install "ndk;25.2.9519653"
RUN /android/sdk/cmdline-tools/latest/bin/sdkmanager --install "build-tools;33.0.2"
RUN /android/sdk/cmdline-tools/latest/bin/sdkmanager --install "platform-tools"
RUN /android/sdk/cmdline-tools/latest/bin/sdkmanager --install "cmake;3.22.1"

# Setup environment variables
ENV JAVA_HOME=/android/studio/jbr
ENV ANDROID_SDK_ROOT=/android/sdk
ENV ANDROID_NDK_HOME=/android/sdk/ndk/25.2.9519653
ENV PATH=${PATH}:/android/sdk/platform-tools:/android/sdk/cmdline-tools/latest/bin

# Mark the /android folder readable to everyone
RUN chmod a+rx /android

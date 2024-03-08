# Container used for minecraft fabric modding development, ~/.gradlew,openjdk
# and fabric project are shared as volumes, JAVA_HOME needs to be assigned to
# openjdk volume, GUI is handled by host wayland display using glfw-patch.
# TODO:
#   - migrate to alpine linux
#   - share pulseaudio socket for audio
#   - use jvm inside container for host kotlin lsp

FROM archlinux:multilib-devel

RUN echo Server = http://archlinux.c3sl.ufpr.br/\$repo/os/\$arch > /etc/pacman.d/mirrorlist
RUN pacman -Syyu --noconfirm
RUN  pacman -Syu --noconfirm && pacman -S --noconfirm sudo base-devel git  lib32-gcc-libs python3 --noconfirm
RUN mkdir -p /tmp/yay-build && useradd -m -G wheel dev && chown -R dev:dev /tmp/yay-build
RUN echo 'dev ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers
USER dev
RUN cd /tmp/yay-build && git clone https://aur.archlinux.org/yay.git /tmp/yay-build/yay
RUN cd /tmp/yay-build/yay && makepkg -si --noconfirm
RUN rm -rf /tmp/yay-build
RUN yes | yay -S glfw-wayland-minecraft portablemc

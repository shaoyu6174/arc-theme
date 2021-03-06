if ENABLE_GTK2
GTK2_SUBDIR = gtk-2.0
endif

if ENABLE_GTK3
GTK3_SUBDIR = gtk-3.0
endif

if ENABLE_XFWM
XFWM_SUBDIR = xfwm4
endif

SUBDIRS = $(GTK2_SUBDIR) $(GTK3_SUBDIR) $(XFWM_SUBDIR)

if ENABLE_LIGHT
theme_DATA = $(srcdir)/index/light/index.theme
endif

if ENABLE_DARKER
themedarker_DATA = $(srcdir)/index/darker/index.theme
endif

if ENABLE_DARK
themedark_DATA = $(srcdir)/index/dark/index.theme
endif

if ENABLE_LIGHTER
themelighter_DATA = $(srcdir)/index/lighter/index.theme
endif


ithemedir        = $(DESTDIR)$(themedir)
ithemedarkerdir  = $(DESTDIR)$(themedarkerdir)
ithemedarkdir    = $(DESTDIR)$(themedarkdir)
ithemelighterdir = $(DESTDIR)$(themelighterdir)

install-exec-hook:

install-data-local:

if ENABLE_CINNAMON
	$(MKDIR_P) $(ithemedir)/cinnamon

	cd $(srcdir)/cinnamon && cp thumbnail.png $(ithemedir)/cinnamon

	$(SASSC) $(srcdir)/cinnamon/$(CINNAMON_VERSION)/sass/cinnamon.scss $(srcdir)/cinnamon/$(CINNAMON_VERSION)/cinnamon.css;

	cd $(srcdir)/cinnamon/$(CINNAMON_VERSION) && cp -R \
		common-assets \
		light-assets \
		cinnamon.css \
		$(ithemedir)/cinnamon

if ENABLE_DARK
	$(MKDIR_P) $(ithemedarkdir)/cinnamon

	cd $(srcdir)/cinnamon && cp thumbnail-dark.png $(ithemedarkdir)/cinnamon/thumbnail.png

	$(SASSC) $(srcdir)/cinnamon/$(CINNAMON_VERSION)/sass/cinnamon-dark.scss $(srcdir)/cinnamon/$(CINNAMON_VERSION)/cinnamon-dark.css;

	cd $(srcdir)/cinnamon/$(CINNAMON_VERSION) && cp -R \
		common-assets \
		dark-assets \
		$(ithemedarkdir)/cinnamon

	cd $(srcdir)/cinnamon/$(CINNAMON_VERSION) && cp -R \
		cinnamon-dark.css \
		$(ithemedarkdir)/cinnamon/cinnamon.css
endif # ENABLE_DARK

endif # ENABLE_GNOME_SHELL


if ENABLE_GNOME_SHELL
	$(MKDIR_P) $(ithemedir)/gnome-shell

if ENABLE_TRANSPARENCY

	$(SASSC) $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/sass/gnome-shell.scss $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/gnome-shell.css;

else !ENABLE_TRANSPARENCY

	$(SASSC) $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/sass/gnome-shell-solid.scss $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/gnome-shell.css;

endif

	cd $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION) && cp -RL \
		common-assets \
		light-assets \
		gnome-shell.css \
		$(ithemedir)/gnome-shell

if ENABLE_DARK
	$(MKDIR_P) $(ithemedarkdir)/gnome-shell

if ENABLE_TRANSPARENCY

	$(SASSC) $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/sass/gnome-shell-dark.scss $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/gnome-shell-dark.css;

else !ENABLE_TRANSPARENCY

	$(SASSC) $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/sass/gnome-shell-solid-dark.scss $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/gnome-shell-dark.css;

endif

	cd $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION) && cp -RL \
		common-assets \
		dark-assets \
		$(ithemedarkdir)/gnome-shell

	cd $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION) && cp -R \
		gnome-shell-dark.css \
		$(ithemedarkdir)/gnome-shell/gnome-shell.css
endif # ENABLE_DARK

if GNOME_SHELL_3_32_OR_NEWER
if ENABLE_LIGHTER
	$(MKDIR_P) $(ithemelighterdir)/gnome-shell

if ENABLE_TRANSPARENCY

	$(SASSC) $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/sass/gnome-shell-lighter.scss $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/gnome-shell-lighter.css;

else !ENABLE_TRANSPARENCY

	$(SASSC) $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/sass/gnome-shell-solid-lighter.scss $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION)/gnome-shell-lighter.css;

endif

	cd $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION) && cp -RL \
		common-assets \
		lighter-assets \
		$(ithemelighterdir)/gnome-shell

	cd $(srcdir)/gnome-shell/$(GNOME_SHELL_VERSION) && cp -R \
		gnome-shell-lighter.css \
		$(ithemelighterdir)/gnome-shell/gnome-shell.css
endif # ENABLE_LIGHTER
endif # GNOME_SHELL_3_32_OR_NEWER

endif # ENABLE_GNOME_SHELL


if ENABLE_METACITY

if ENABLE_LIGHT
	cp -R $(srcdir)/metacity-1 $(ithemedir)

	cd $(ithemedir)/metacity-1 && rm metacity-theme-1-dark.xml metacity-theme-2-dark.xml thumbnail-dark.png
endif # ENABLE_LIGHT

if ENABLE_DARKER
	cp -R $(srcdir)/metacity-1 $(ithemedarkerdir)

	cd $(ithemedarkerdir)/metacity-1 && \
		mv metacity-theme-1-dark.xml metacity-theme-1.xml && \
		mv metacity-theme-2-dark.xml metacity-theme-2.xml && \
		mv thumbnail-dark.png thumbnail.png
endif # ENABLE_DARKER

if ENABLE_DARK
	cp -R $(srcdir)/metacity-1 $(ithemedarkdir)

	cd $(ithemedarkdir)/metacity-1 && \
		mv metacity-theme-1-dark.xml metacity-theme-1.xml && \
		mv metacity-theme-2-dark.xml metacity-theme-2.xml && \
		mv thumbnail-dark.png thumbnail.png
endif # ENABLE_DARK

if ENABLE_LIGHTER
	cp -R $(srcdir)/metacity-1 $(ithemelighterdir)

	cd $(ithemelighterdir)/metacity-1 && rm metacity-theme-1-dark.xml metacity-theme-2-dark.xml thumbnail-dark.png
endif # ENABLE_LIGHTER

endif # ENABLE_METACITY

if ENABLE_OPENBOX

if ENABLE_LIGHT
	cp -R $(srcdir)/openbox/Arc/* $(ithemedir)
endif # ENABLE_LIGHT

if ENABLE_DARKER
	cp -R $(srcdir)/openbox/Arc-Darker/* $(ithemedarkerdir)
endif # ENABLE_DARKER

if ENABLE_DARK
	cp -R $(srcdir)/openbox/Arc-Dark/* $(ithemedarkdir)
endif # ENABLE_DARK

endif # ENABLE_OPENBOX


if ENABLE_UNITY

if ENABLE_LIGHT
	cp -R $(srcdir)/unity $(ithemedir)

	cd $(ithemedir)/unity && rm -rf window-buttons-dark
endif # ENABLE_LIGHT

if ENABLE_DARKER
	cp -R $(srcdir)/unity $(ithemedarkerdir)

	cd $(ithemedarkerdir)/unity && \
	rm -rf window-buttons && \
	mv window-buttons-dark window-buttons
endif # ENABLE_DARKER

if ENABLE_DARK
	cp -R $(srcdir)/unity $(ithemedarkdir)

	cd $(ithemedarkdir)/unity && \
	rm -rf window-buttons && \
	mv window-buttons-dark window-buttons
endif # ENABLE_DARK

if ENABLE_LIGHTER
	cp -R $(srcdir)/unity $(ithemelighterdir)

	cd $(ithemelighterdir)/unity && rm -rf window-buttons-dark
endif # ENABLE_LIGHTER

endif # ENABLE_UNITY


if ENABLE_PLANK

if ENABLE_LIGHT
	cp -R $(srcdir)/plank $(ithemedir)

	cd $(ithemedir)/plank && rm dock-lighter.theme
endif # ENABLE_LIGHT

if ENABLE_DARKER
	cp -R $(srcdir)/plank $(ithemedarkerdir)

	cd $(ithemedarkerdir)/plank && rm dock-lighter.theme
endif # ENABLE_DARKER

if ENABLE_DARK
	cp -R $(srcdir)/plank $(ithemedarkdir)

	cd $(ithemedarkdir)/plank && rm dock-lighter.theme
endif # ENABLE_DARK

if ENABLE_LIGHTER
	cp -R $(srcdir)/plank $(ithemelighterdir)

	cd $(ithemelighterdir)/plank && \
	rm dock.theme && \
	mv dock-lighter.theme dock.theme
endif # ENABLE_LIGHTER

endif # ENABLE_PLANK


uninstall-local:
	rm -rf $(ithemedir)

if ENABLE_DARKER
	rm -rf $(ithemedarkerdir)
endif # ENABLE_DARKER

if ENABLE_DARK
	rm -rf $(ithemedarkdir)
endif # ENABLE_DARK

if ENABLE_LIGHTER
	rm -rf $(ithemelighterdir)
endif # ENABLE_LIGHTER


EXTRA_DIST = \
	cinnamon \
	gnome-shell \
	index \
	metacity-1 \
	unity \
	plank

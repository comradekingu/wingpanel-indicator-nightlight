project('nightlight', 'vala', 'c')

gettext_name = meson.project_name() + '-indicator'
gnome = import('gnome')
i18n = import('i18n')

add_global_arguments('-DGETTEXT_PACKAGE="@0@"'.format(gettext_name), language:'c')

asresources = gnome.compile_resources(
    'as-resources', 'data/io.elementary.wingpanel.nightlight.gresource.xml',
    source_dir: 'data',
    c_name: 'as'
)

wingpanel_dep = dependency('wingpanel-2.0')

shared_module(
    meson.project_name(),
    'src/Indicator.vala',
    'src/Services/ColorInterface.vala',
    'src/Widgets/PopoverWidget.vala',
    'src/Widgets/RevealerSwitch.vala',
    asresources,
    dependencies: [
        dependency('glib-2.0'),
        dependency('gobject-2.0'),
        dependency('granite'),
        dependency('gtk+-3.0'),
        wingpanel_dep
    ],
    install: true,
    install_dir : wingpanel_dep.get_pkgconfig_variable('indicatorsdir')
)

subdir('po')

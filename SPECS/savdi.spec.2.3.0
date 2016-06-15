%define debug_package          %{nil}
%define dir_sav_install        /opt/sophos-av
%define name_daemon            savdid

Name: savdi
Version: 2.3.0
Release: 0
Group: System Environment/Daemons
URL: https://www.sophos.com/
License: Copyright 2000-2015 Sophos Limited. All rights reserved
Source0: %{name}-23-linux-64bit.tar
Source1: savdid.init
Summary: Sophos Anti-Virus Dynamic Interface
BuildRoot: %{_tmppath}/%{name}-%{version}-%{release}-root-%(%{__id_u} -n)
AutoReqProv: no
Requires: glibc savinstpkg

%description
Sophos Anti-Virus Dynamic Interface

%prep
%setup -q -n savdi-install

%build
:

%install
%{__rm} -rf ${RPM_BUILD_ROOT}
%{__mkdir} -p ${RPM_BUILD_ROOT}%{_sysconfdir}/%{name}
%{__mkdir} -p ${RPM_BUILD_ROOT}%{_sysconfdir}/init.d
%{__mkdir} -p ${RPM_BUILD_ROOT}/%{_lib}
%{__mkdir} -p ${RPM_BUILD_ROOT}%{_mandir}/man1
%{__mkdir} -p ${RPM_BUILD_ROOT}%{dir_sav_install}/%{name}

%{__install} -m 0755 %{name_daemon} ${RPM_BUILD_ROOT}%{dir_sav_install}/%{name}/
%{__install} -m 0644 %{name_daemon}.conf ${RPM_BUILD_ROOT}%{_sysconfdir}/%{name}/
%{__install} -m 0644 %{name_daemon}lang_en.txt ${RPM_BUILD_ROOT}%{_sysconfdir}/%{name}/
%{__install} -m 0755 %{SOURCE1} ${RPM_BUILD_ROOT}%{_sysconfdir}/init.d/%{name_daemon}

%{__ln_s} %{dir_sav_install}/%{_lib}/libssp.so.0 ${RPM_BUILD_ROOT}/%{_lib}/libssp.so.0
%{__ln_s} %{dir_sav_install}/%{_lib}/libsavi.so.3 ${RPM_BUILD_ROOT}/%{_lib}/libsavi.so.3

%clean
%{__rm} -rf ${RPM_BUILD_ROOT}

%files
%defattr(-,root,root,-)
%doc readsavdi_eng.txt savdi_licence_en.txt EULA.rtf
%dir %{_sysconfdir}/%{name}
%config(noreplace) %{_sysconfdir}/%{name}/%{name_daemon}.conf
%{_sysconfdir}/%{name}/%{name_daemon}lang_en.txt
%{_sysconfdir}/init.d/%{name_daemon}
%dir %{dir_sav_install}/%{name}
%{dir_sav_install}/%{name}/%{name_daemon}
/%{_lib}/libssp.so.0
/%{_lib}/libsavi.so.3

%changelog
* Sat Jun 11 2016 nazx <jjj@nazx.jp> - 2.3.0
- Initial release


project('mosquitto', 'c', version : '1.6.9')

with_tls = get_option('with-tls')

if with_tls
  add_project_arguments('-DWITH_TLS', language : 'c')
endif

if get_option('with-tls-psk')
  with_tls = true
  with_tls_psk = true
  add_project_arguments('-DWITH_TLS_PSK', language : 'c')
endif

if get_option('with-ec')
  with_tls = true
  add_project_arguments('-DWITH_EC', language : 'c')
endif

openssl_dep = dependency('openssl', required : with_tls)

with_socks = get_option('with-socks')
if with_socks
  add_project_arguments('-DWITH_SOCKS', language : 'c')
endif

with_threading = get_option('with-threading')
if with_threading
  add_project_arguments('-DWITH_THREADING', language : 'c')
endif
threading_dep = dependency('threads', required : with_threading)

with_dlt = get_option('with-dlt')
if with_dlt
  dlt_dep = dependency('automotive-dlt', version : '>=2.11', required : true)
  add_project_arguments('-DWITH_DLT', language : 'c')
endif

subdir('lib')

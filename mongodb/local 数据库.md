# local 数据库
每个 Mongodb 实例里都有一个名为 `local` 的数据库,主要是存储复制过程中的数据和一些实例特有的数据。

`local` 数据库下有个 `startup_log` 集合，每次启动的时候，它都会插入文档。这个集合是个固定集合，也就是达到限制的时候，旧的数据会被覆盖。

```shell
test> use local
switched to db local
local> show collections;
startup_log
local> db.startup_log.find()
[
  {
    _id: 'e04f73deb2c7-1707964528897',
    hostname: 'e04f73deb2c7',
    startTime: ISODate('2024-02-15T02:35:28.000Z'),
    startTimeLocal: 'Thu Feb 15 02:35:28.897',
    cmdLine: { net: { bindIp: '*' } },
    pid: Long('1'),
    buildinfo: {
      version: '7.0.5',
      gitVersion: '7809d71e84e314b497f282ea8aa06d7ded3eb205',
      modules: [],
      allocator: 'tcmalloc',
      javascriptEngine: 'mozjs',
      sysInfo: 'deprecated',
      versionArray: [ 7, 0, 5, 0 ],
      openssl: {
        running: 'OpenSSL 3.0.2 15 Mar 2022',
        compiled: 'OpenSSL 3.0.2 15 Mar 2022'
      },
      buildEnvironment: {
        distmod: 'ubuntu2204',
        distarch: 'aarch64',
        cc: '/opt/mongodbtoolchain/v4/bin/gcc: gcc (GCC) 11.3.0',
        ccflags: '-Werror -include mongo/platform/basic.h -ffp-contract=off -fasynchronous-unwind-tables -g2 -Wall -Wsign-compare -Wno-unknown-pragmas -Winvalid-pch -gdwarf-5 -fno-omit-frame-pointer -fno-strict-aliasing -O2 -march=armv8.2-a -mtune=generic -Wno-unused-local-typedefs -Wno-unused-function -Wno-deprecated-declarations -Wno-unused-const-variable -Wno-unused-but-set-variable -Wno-missing-braces -fstack-protector-strong -gdwarf64 -Wa,--nocompress-debug-sections -Wimplicit-fallthrough=5',
        cxx: '/opt/mongodbtoolchain/v4/bin/g++: g++ (GCC) 11.3.0',
        cxxflags: '-Woverloaded-virtual -Wpessimizing-move -Wno-maybe-uninitialized -fsized-deallocation -Wno-deprecated -std=c++20',
        linkflags: '-Wl,--fatal-warnings -B/opt/mongodbtoolchain/v4/bin -gdwarf-5 -pthread -Wl,-z,now -fuse-ld=lld -fstack-protector-strong -gdwarf64 -Wl,--build-id -Wl,--hash-style=gnu -Wl,-z,noexecstack -Wl,--warn-execstack -Wl,-z,relro -Wl,--compress-debug-sections=none -Wl,-z,origin -Wl,--enable-new-dtags',
        target_arch: 'aarch64',
        target_os: 'linux',
        cppdefines: 'SAFEINT_USE_INTRINSICS 0 PCRE2_STATIC NDEBUG _XOPEN_SOURCE 700 _GNU_SOURCE _FORTIFY_SOURCE 2 ABSL_FORCE_ALIGNED_ACCESS BOOST_ENABLE_ASSERT_DEBUG_HANDLER BOOST_FILESYSTEM_NO_CXX20_ATOMIC_REF BOOST_LOG_NO_SHORTHAND_NAMES BOOST_LOG_USE_NATIVE_SYSLOG BOOST_LOG_WITHOUT_THREAD_ATTR BOOST_MATH_NO_LONG_DOUBLE_MATH_FUNCTIONS BOOST_SYSTEM_NO_DEPRECATED BOOST_THREAD_USES_DATETIME BOOST_THREAD_VERSION 5'
      },
      bits: 64,
      debug: false,
      maxBsonObjectSize: 16777216,
      storageEngines: [ 'devnull', 'wiredTiger' ]
    }
  }
]
```
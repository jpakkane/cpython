project('python', 'c',
  default_options : ['c_std=c99'])

cc = meson.get_compiler('c')

thread_dep = dependency('threads')
m_dep = cc.find_library('m', required : false)

cdata = configuration_data()
check_headers = [
  ['HAVE_ALLOCA_H', 'alloca.h'],
  ['HAVE_ASM_TYPES_H', 'asm/types.h'],
  ['HAVE_BLUETOOTH_BLUETOOTH_H', 'bluetooth/bluetooth.h'],
  ['HAVE_BLUETOOTH_H', 'bluetooth.h'],
  ['HAVE_CONIO_H', 'conio.h'],
  ['HAVE_CURSES_H', 'curses.h'],
  ['HAVE_DIRECT_H', 'direct.h'],
  ['HAVE_DIRENT_H', 'dirent.h'],
  ['HAVE_DLFCN_H', 'dlfcn.h'],
  ['HAVE_ENDIAN_H', 'endian.h'],
  ['HAVE_ERRNO_H', 'errno.h'],
  ['HAVE_FCNTL_H', 'fcntl.h'],
  ['HAVE_GRP_H', 'grp.h'],
  ['HAVE_IEEEFP_H', 'ieeefp.h'],
  ['HAVE_INTTYPES_H', 'inttypes.h'],
  ['HAVE_IO_H', 'io.h'],
  ['HAVE_LANGINFO_H', 'langinfo.h'],
  ['HAVE_LIBINTL_H', 'libintl.h'],
  ['HAVE_LIBUTIL_H', 'libutil.h'],
  ['HAVE_LINUX_CAN_BCM_H', 'linux/can/bcm.h'],
  ['HAVE_LINUX_CAN_H', 'linux/can.h'],
  ['HAVE_LINUX_CAN_RAW_H', 'linux/can/raw.h'],
  ['HAVE_LINUX_NETLINK_H', 'linux/netlink.h'],
  ['HAVE_LINUX_RANDOM_H', 'linux/random.h'],
  ['HAVE_LINUX_TIPC_H', 'linux/tipc.h'],
  ['HAVE_MEMORY_H', 'memory.h'],
  ['HAVE_NCURSES_H', 'ncurses.h'],
  ['HAVE_NDIR_H', 'ndir.h'],
  ['HAVE_NETPACKET_PACKET_H', 'netpacket/packet.h'],
  ['HAVE_NET_IF_H', 'net/if.h'],
  ['HAVE_POLL_H', 'poll.h'],
  ['HAVE_PROCESS_H', 'process.h'],
  ['HAVE_PTHREAD_H', 'pthread.h'],
  ['HAVE_PTY_H', 'pty.h'],
  ['HAVE_SCHED_H', 'sched.h'],
  ['HAVE_SHADOW_H', 'shadow.h'],
  ['HAVE_SIGNAL_H', 'signal.h'],
  ['HAVE_SPAWN_H', 'spawn.h'],
  ['HAVE_STDINT_H', 'stdint.h'],
  ['HAVE_STDLIB_H', 'stdlib.h'],
  ['HAVE_STRINGS_H', 'strings.h'],
  ['HAVE_STRING_H', 'string.h'],
  ['HAVE_STROPTS_H', 'stropts.h'],
  ['HAVE_SYSEXITS_H', 'sysexits.h'],
  ['HAVE_SYS_AUDIOIO_H', 'sys/audioio.h'],
  ['HAVE_SYS_BSDTTY_H', 'sys/bsdtty.h'],
  ['HAVE_SYS_DEVPOLL_H', 'sys/devpoll.h'],
  ['HAVE_SYS_DIR_H', 'sys/dir.h'],
  ['HAVE_SYS_ENDIAN_H', 'sys/endian.h'],
  ['HAVE_SYS_EPOLL_H', 'sys/epoll.h'],
  ['HAVE_SYS_EVENT_H', 'sys/event.h'],
  ['HAVE_SYS_FILE_H', 'sys/file.h'],
  ['HAVE_SYS_IOCTL_H', 'sys/ioctl.h'],
  ['HAVE_SYS_KERN_CONTROL_H', 'sys/kern/control.h'],
  ['HAVE_SYS_LOADAVG_H', 'sys/loadavg.h'],
  ['HAVE_SYS_LOCK_H', 'sys/lock.h'],
  ['HAVE_SYS_MKDEV_H', 'sys/mkdev.h'],
  ['HAVE_SYS_MODEM_H', 'sys/modem.h'],
  ['HAVE_SYS_NDIR_H', 'sys/ndir.h'],
  ['HAVE_SYS_PARAM_H', 'sys/param.h'],
  ['HAVE_SYS_POLL_H', 'sys/poll.h'],
  ['HAVE_SYS_RANDOM_H', 'sys/random.h'],
  ['HAVE_SYS_RESOURCE_H', 'sys/resource.h'],
  ['HAVE_SYS_SELECT_H', 'sys/select.h'],
  ['HAVE_SYS_SENDFILE_H', 'sys/sendfile.h'],
  ['HAVE_SYS_SOCKET_H', 'sys/socket.h'],
  ['HAVE_SYS_STATVFS_H', 'sys/statvfs.h'],
  ['HAVE_SYS_STAT_H', 'sys/stat.h'],
  ['HAVE_SYS_SYSCALL_H', 'sys/syscall.h'],
  ['HAVE_SYS_SYS_DOMAIN_H', 'sys/sys/domain.h'],
  ['HAVE_SYS_TERMIO_H', 'sys/termio.h'],
  ['HAVE_SYS_TIMES_H', 'sys/times.h'],
  ['HAVE_SYS_TIME_H', 'sys/time.h'],
  ['HAVE_SYS_TYPES_H', 'sys/types.h'],
  ['HAVE_SYS_UIO_H', 'sys/uio.h'],
  ['HAVE_SYS_UN_H', 'sys/un.h'],
  ['HAVE_SYS_UTSNAME_H', 'sys/utsname.h'],
  ['HAVE_SYS_WAIT_H', 'sys/wait.h'],
  ['HAVE_SYS_XATTR_H', 'sys/xattr.h'],
  ['HAVE_TERMIOS_H', 'termios.h'],
  ['HAVE_TERM_H', 'term.h'],
  ['HAVE_UNISTD_H', 'unistd.h'],
  ['HAVE_UTIL_H', 'util.h'],
  ['HAVE_UTIME_H', 'utime.h'],
  ['HAVE_WCHAR_H', 'wchar.h'],
]

foreach h : check_headers
  if cc.has_header(h.get(1))
    cdata.set(h.get(0), 1)
  endif
endforeach

check_functions = [
  ['HAVE_ACCEPT4', 'accept4', '#include<sys/socket.h>'],
  ['HAVE_ACOSH', 'acosh', '#include<math.h>'],
# check token ('HAVE_ADDRINFO',)
  ['HAVE_ALARM', 'alarm', '#include<unistd.h>'],
# check token ('HAVE_ALIGNED_REQUIRED',)
# check token ('HAVE_ALTZONE',)
  ['HAVE_ASINH', 'asinh', '#include<math.h>'],
  ['HAVE_ATANH', 'atanh', '#include<math.h>'],
# check token ('HAVE_BIND_TEXTDOMAIN_CODESET',)
# check token ('HAVE_BROKEN_MBSTOWCS',)
# check token ('HAVE_BROKEN_NICE',)
# check token ('HAVE_BROKEN_PIPE_BUF',)
# check token ('HAVE_BROKEN_POLL',)
# check token ('HAVE_BROKEN_POSIX_SEMAPHORES',)
# check token ('HAVE_BROKEN_PTHREAD_SIGMASK',)
# check token ('HAVE_BROKEN_SEM_GETVALUE',)
# check token ('HAVE_BROKEN_UNSETENV',)
# check token ('HAVE_BUILTIN_ATOMIC',)
# check token ('HAVE_CHFLAGS',)
  ['HAVE_CHOWN', 'chown', '#include<unistd.h>'],
  ['HAVE_CHROOT', 'chroot', '#include<unistd.h>'],
  ['HAVE_CLOCK', 'clock', '#include<time.h>'],
  ['HAVE_CLOCK_GETRES', 'clock_getres', '#include<time.h>'],
  ['HAVE_CLOCK_GETTIME', 'clock_gettime', '#include<time.h>'],
  ['HAVE_CLOCK_SETTIME', 'clock_settime', '#include<time.h>'],
# check token ('HAVE_COMPUTED_GOTOS',)
  ['HAVE_CONFSTR', 'confstr', '#include<time.h>'],
  ['HAVE_COPYSIGN', 'copysign', '#include<math.h>'],
  ['HAVE_CTERMID', 'ctermid', '#include<stdio.h>'],
# check token ('HAVE_CTERMID_R',)
# check token ('HAVE_CURSES_IS_TERM_RESIZED',)
# check token ('HAVE_CURSES_RESIZETERM',)
# check token ('HAVE_CURSES_RESIZE_TERM',)
# check token ('HAVE_DECL_ISFINITE',)
  ['HAVE_DECL_ISINF', 'isinf', '#include<math.h>'],
  ['HAVE_DECL_ISNAN', 'isnan', '#include<math.h>'],
# check token ('HAVE_DECL_RTLD_DEEPBIND',)
# check token ('HAVE_DECL_RTLD_GLOBAL',)
# check token ('HAVE_DECL_RTLD_LAZY',)
# check token ('HAVE_DECL_RTLD_LOCAL',)
# check token ('HAVE_DECL_RTLD_NODELETE',)
# check token ('HAVE_DECL_RTLD_NOLOAD',)
# check token ('HAVE_DECL_RTLD_NOW',)
# check token ('HAVE_DECL_TZNAME',)
# check token ('HAVE_DEVICE_MACROS',)
# check token ('HAVE_DEV_PTC',)
# check token ('HAVE_DEV_PTMX',)
# check token ('HAVE_DIRENT_D_TYPE',)
  ['HAVE_DIRFD', 'dirfd', '#include<dirent.h>'],
#  ['HAVE_DLOPEN', 'dlopen', '#include<dlfcn.h>'],
  ['HAVE_DUP2', 'dup2', '#include<unistd.h>'],
  ['HAVE_DUP3', 'dup3', '#include<unistd.h>'],
# check token ('HAVE_DYNAMIC_LOADING',)
# check token ('HAVE_EPOLL',)
  ['HAVE_EPOLL_CREATE1', 'epoll_create1', '#include<sys/epoll.h>'],
  ['HAVE_ERF', 'erf', '#include<math.h>'],
  ['HAVE_ERFC', 'erfc', '#include<math.h>'],
  ['HAVE_EXECV', 'execv', '#include<unistd.h>'],
  ['HAVE_EXPM1', 'expm1', '#include<math.h>'],
  ['HAVE_FACCESSAT', 'faccessat', '#include<unistd.h>'],
  ['HAVE_FCHDIR', 'fchdir', '#include<unistd.h>'],
  ['HAVE_FCHMOD', 'fchmod', '#include<sys/stat.h>'],
  ['HAVE_FCHMODAT', 'fchmodat', '#include<sys/stat.h>'],
  ['HAVE_FCHOWN', 'fchown', '#include<unistd.h>'],
# check token ('HAVE_FCHOWNAT',)
  ['HAVE_FDATASYNC', 'fdatasync', '#include<unistd.h>'],
  ['HAVE_FDOPENDIR', 'fdopendir', '#include<dirent.h>'],
  ['HAVE_FEXECVE', 'fexecve', '#include<unistd.h>'],
  ['HAVE_FINITE', 'finite', '#include<math.h>'],
  ['HAVE_FLOCK', 'flock', '#include<sys/file.h>'],
  ['HAVE_FORK', 'fork', '#include<unistd.h>'],
  ['HAVE_FORKPTY', 'forkpty', '#include<pty.h>'],
  ['HAVE_FPATHCONF', 'fpathconf', '#include<unistd.h>'],
# check token ('HAVE_FSEEK64',)
  ['HAVE_FSEEKO', 'fseeko', '#include<stdio.h>'],
  ['HAVE_FSTATAT', 'fstatat', '#include<unistd.h>'],
  ['HAVE_FSTATVFS', 'fstatvfs', '#include<sys/statvfs.h>'],
  ['HAVE_FSYNC', 'fsync', '#include<unistd.h>'],
# check token ('HAVE_FTELL64',)
  ['HAVE_FTELLO', 'ftello', '#include<stdio.h>'],
  ['HAVE_FTIME', 'ftime', '#include<sys/timeb.h>'],
  ['HAVE_FTRUNCATE', 'ftruncate', '#include<unistd.h>'],
  ['HAVE_FUTIMENS', 'futimens', '#include<sys/stat.h>'],
  ['HAVE_FUTIMES', 'futimes', '#include<sys/time.h>'],
  ['HAVE_FUTIMESAT', 'futimesat', '#include<sys/time.h>'],
  ['HAVE_GAI_STRERROR', 'gai_strerror', '#include<netdb.h>'],
  ['HAVE_GAMMA', 'gamma', '#include<math.h>'],
# check token ('HAVE_GCC_ASM_FOR_MC68881',)
# check token ('HAVE_GCC_ASM_FOR_X64',)
# check token ('HAVE_GCC_ASM_FOR_X87',)
# check token ('HAVE_GCC_UINT128_T',)
  ['HAVE_GETADDRINFO', 'getaddrinfo', '#include<netdb.h>'],
  ['HAVE_GETC_UNLOCKED', 'getc_unlocked', '#include<stdio.h>'],
# check token ('HAVE_GETENTROPY',)
  ['HAVE_GETGROUPLIST', 'getgrouplist', '#include<grp.h>'],
  ['HAVE_GETGROUPS', 'getgroups', '#include<grp.h>'],
  ['HAVE_GETHOSTBYNAME', 'gethostbyname', '#include<netdb.h>'],
  ['HAVE_GETHOSTBYNAME_R', 'gethostbyname_r', '#include<netdb.h>'],
# check token ('HAVE_GETHOSTBYNAME_R_3_ARG',)
# check token ('HAVE_GETHOSTBYNAME_R_5_ARG',)
# check token ('HAVE_GETHOSTBYNAME_R_6_ARG',)
  ['HAVE_GETITIMER', 'getitimer', '#include<sys/time.h>'],
  ['HAVE_GETLOADAVG', 'getloadavg', '#include<stdlib.h>'],
  ['HAVE_GETLOGIN', 'getlogin', '#include<unistd.h>'],
  ['HAVE_GETNAMEINFO', 'getnameinfo', '#include<netdb.h>'],
  ['HAVE_GETPAGESIZE', 'getpagesize', '#include<unistd.h>'],
  ['HAVE_GETPEERNAME', 'getpeername', '#include<sys/socket.h>'],
  ['HAVE_GETPGID', 'getpgid', '#include<unistd.h>'],
  ['HAVE_GETPGRP', 'getpgrp', '#include<unistd.h>'],
  ['HAVE_GETPID', 'getpid', '#include<unistd.h>'],
  ['HAVE_GETPRIORITY', 'getpriority', '#include<sys/resource.h>'],
  ['HAVE_GETPWENT', 'getpwent', '#include<pwd.h>'],
  ['HAVE_GETRANDOM', 'getrandom', '#include<linux/random.h>'],
# check token ('HAVE_GETRANDOM_SYSCALL',)
  ['HAVE_GETRESGID', 'getresgid', '#include<unistd.h>'],
  ['HAVE_GETRESUID', 'getresuid', '#include<unistd.h>'],
  ['HAVE_GETSID', 'getsid', '#include<unistd.h>'],
  ['HAVE_GETSPENT', 'getspent', '#include<shadow.h>'],
  ['HAVE_GETSPNAM', 'getspnam', '#include<shadow.h>'],
  ['HAVE_GETTIMEOFDAY', 'gettimeofday', '#include<sys/time.h>'],
  ['HAVE_GETWD', 'getwd', '#include<unistd.h>'],
# check token ('HAVE_GLIBC_MEMMOVE_BUG',)
  ['HAVE_HSTRERROR', 'hstrerror', '#include<netdb.h>'],
  ['HAVE_HTOLE64', 'htole64', '#include<endian.h>'],
  ['HAVE_HYPOT', 'hypot', '#include<math.h>'],
  ['HAVE_IF_NAMEINDEX', 'if_nameindex', '#include<net/if.h>'],
  ['HAVE_INET_ATON', 'inet_aton', '#include<arpa/inet.h>'],
  ['HAVE_INET_PTON', 'inet_pton', '#include<arpa/inet.h>'],
  ['HAVE_INITGROUPS', 'initgroups', '#include<grp.h>'],
# check token ('HAVE_IPA_PURE_CONST_BUG',)
  ['HAVE_KILL', 'kill', '#include<signal.h>'],
  ['HAVE_KILLPG', 'killpg', '#include<signal.h>'],
  ['HAVE_KQUEUE', 'kqueue', '#include<sys/event.h>'],
# check token ('HAVE_LARGEFILE_SUPPORT',)
# check token ('HAVE_LCHFLAGS',)
  ['HAVE_LCHMOD', 'lchmod', '#include<sys/stat.h>'],
  ['HAVE_LCHOWN', 'lchown', '#include<unistd.h>'],
  ['HAVE_LGAMMA', 'lgamma', '#include<math.h>'],
# check token ('HAVE_LIBDL',)
# check token ('HAVE_LIBDLD',)
# check token ('HAVE_LIBIEEE',)
# check token ('HAVE_LIBREADLINE',)
# check token ('HAVE_LIBRESOLV',)
# check token ('HAVE_LIBSENDFILE',)
  ['HAVE_LINK', 'link', '#include<unistd.h>'],
  ['HAVE_LINKAT', 'linkat', '#include<unistd.h>'],
# check token ('HAVE_LINUX_CAN_RAW_FD_FRAMES',)
  ['HAVE_LOCKF', 'lockf', '#include<unistd.h>'],
  ['HAVE_LOG1P', 'log1p', '#include<math.h>'],
  ['HAVE_LOG2', 'log2', '#include<math.h>'],
# check token ('HAVE_LONG_DOUBLE',)
  ['HAVE_LSTAT', 'lstat', '#include<sys/stat.h>'],
  ['HAVE_LUTIMES', 'lutimes', '#include<sys/time.h>'],
  ['HAVE_MAKEDEV', 'makedev', '#include<sys/sysmacros.h>'],
  ['HAVE_MBRTOWC', 'mbrtowc', '#include<wchar.h>'],
  ['HAVE_MEMMOVE', 'memmove', '#include<string.h>'],
  ['HAVE_MEMRCHR', 'memrchr', '#include<string.h>'],
  ['HAVE_MKDIRAT', 'mkdirat', '#include<sys/stat.h>'],
  ['HAVE_MKFIFO', 'mkfifo', '#include<sys/stat.h>'],
  ['HAVE_MKFIFOAT', 'mkfifoat', '#include<sys/stat.h>'],
  ['HAVE_MKNOD', 'mknod', '#include<unistd.h>'],
  ['HAVE_MKNODAT', 'mknodat', '#include<unistd.h>'],
  ['HAVE_MKTIME', 'mktime', '#include<unistd.h>'],
  ['HAVE_MMAP', 'mmap', '#include<sys/mman.h>'],
# check token ('HAVE_MREMAP',)
  ['HAVE_NICE', 'nice', '#include<unistd.h>'],
  ['HAVE_OPENAT', 'openat', '#include<fcntl.h>'],
  ['HAVE_OPENPTY', 'openpty', '#include<pty.h>'],
  ['HAVE_PATHCONF', 'pathconf', '#include<unistd.h>'],
  ['HAVE_PAUSE', 'pause', '#include<unistd.h>'],
  ['HAVE_PIPE2', 'pipe2', '#include<fcntl.h>'],
# check token ('HAVE_PLOCK',)
  ['HAVE_POLL', 'poll', '#include<poll.h>'],
# check token ('HAVE_POSIX_FADVISE',)
# check token ('HAVE_POSIX_FALLOCATE',)
  ['HAVE_PREAD', 'pread', '#include<unistd.h>'],
  ['HAVE_PRLIMIT', 'prlimit', '#include<sys/resource.h>'],
# check token ('HAVE_PROTOTYPES',)
# check token ('HAVE_PTHREAD_ATFORK',)
# check token ('HAVE_PTHREAD_DESTRUCTOR',)
# check token ('HAVE_PTHREAD_INIT',)
  ['HAVE_PTHREAD_KILL', 'pthread_kill', '#include<signal.h>'],
  ['HAVE_PTHREAD_SIGMASK', 'pthread_sigmask', '#include<signal.h>'],
  ['HAVE_PUTENV', 'putenv', '#include<stdlib.h>'],
  ['HAVE_PWRITE', 'pwrite', '#include<unistd.h>'],
  ['HAVE_READLINK', 'readlink', '#include<unistd.h>'],
  ['HAVE_READLINKAT', 'readlinkat', '#include<unistd.h>'],
  ['HAVE_READV', 'readv', '#include<sys/uio.h>'],
# check token ('HAVE_REALPATH',)
  ['HAVE_RENAMEAT', 'renamat', '#include<stdio.h>'],
# check token ('HAVE_RL_APPEND_HISTORY',)
# check token ('HAVE_RL_CALLBACK',)
# check token ('HAVE_RL_CATCH_SIGNAL',)
# check token ('HAVE_RL_COMPLETION_APPEND_CHARACTER',)
# check token ('HAVE_RL_COMPLETION_DISPLAY_MATCHES_HOOK',)
# check token ('HAVE_RL_COMPLETION_MATCHES',)
# check token ('HAVE_RL_COMPLETION_SUPPRESS_APPEND',)
# check token ('HAVE_RL_PRE_INPUT_HOOK',)
# check token ('HAVE_RL_RESIZE_TERMINAL',)
  ['HAVE_ROUND', 'round', '#include<math.h>'],
  ['HAVE_SCHED_GET_PRIORITY_MAX', 'sched_get_priority_max', '#include<sched.h>'],
  ['HAVE_SCHED_RR_GET_INTERVAL', 'sched_rr_get_interval', '#include<sched.h>'],
  ['HAVE_SCHED_SETAFFINITY', 'sched_setaffinity', '#include<sched.h>'],
  ['HAVE_SCHED_SETPARAM', 'sched_setparam', '#include<sched.h>'],
  ['HAVE_SCHED_SETSCHEDULER', 'sched_setscheduler', '#include<sched.h>'],
  ['HAVE_SELECT', 'select', '#include<sys/select.h>'],
  ['HAVE_SEM_GETVALUE', 'sem_getvalue', '#include<semaphore.h>'],
  ['HAVE_SEM_OPEN', 'sem_open', '#include<semaphore.h>'],
  ['HAVE_SEM_TIMEDWAIT', 'sem_timedwait', '#include<semaphore.h>'],
  ['HAVE_SEM_UNLINK', 'sem_unlink', '#include<semaphore.h>'],
  ['HAVE_SENDFILE', 'sendfile', '#include<sys/sendfile.h>'],
  ['HAVE_SETEGID', 'setegid', '#include<unistd.h>'],
  ['HAVE_SETEUID', 'seteuid', '#include<unistd.h>'],
  ['HAVE_SETGID', 'setgid', '#include<unistd.h>'],
  ['HAVE_SETGROUPS', 'setgroups', '#include<grp.h>'],
  ['HAVE_SETHOSTNAME', 'sethostname', '#include<unistd.h>'],
  ['HAVE_SETITIMER', 'setitimer', '#include<sys/time.h>'],
  ['HAVE_SETLOCALE', 'setlocale', '#include<locale.h>'],
  ['HAVE_SETPGID', 'setpgid', '#include<unistd.h>'],
  ['HAVE_SETPGRP', 'setpgrp', '#include<unistd.h>'],
  ['HAVE_SETPRIORITY', 'setpriority', '#include<sys/resource.h>'],
  ['HAVE_SETREGID', 'setregid', '#include<unistd.h>'],
  ['HAVE_SETRESGID', 'setresgid', '#include<unistd.h>'],
  ['HAVE_SETRESUID', 'setresuid', '#include<unistd.h>'],
  ['HAVE_SETREUID', 'setreuid', '#include<unistd.h>'],
  ['HAVE_SETSID', 'setsid', '#include<unistd.h>'],
  ['HAVE_SETUID', 'setuid', '#include<unistd.h>'],
  ['HAVE_SETVBUF', 'setvbuf', '#include<unistd.h>'],
  ['HAVE_SIGACTION', 'sigaction', '#include<signal.h>'],
  ['HAVE_SIGALTSTACK', 'sigaltstack', '#include<signal.h>'],
# check token ('HAVE_SIGINFO_T_SI_BAND',)
  ['HAVE_SIGINTERRUPT', 'siginterrupt', '#include<signal.h>'],
  ['HAVE_SIGPENDING', 'sigpending', '#include<signal.h>'],
  ['HAVE_SIGRELSE', 'sigrelse', '#include<signal.h>'],
  ['HAVE_SIGTIMEDWAIT', 'sigtimedwait', '#include<signal.h>'],
  ['HAVE_SIGWAIT', 'sigwait', '#include<signal.h>'],
  ['HAVE_SIGWAITINFO', 'sigwaitinfo', '#include<signal.h>'],
  ['HAVE_SNPRINTF', 'snprintf', '#include<stdio.h>'],
# check token ('HAVE_SOCKADDR_ALG',)
# check token ('HAVE_SOCKADDR_SA_LEN',)
# check token ('HAVE_SOCKADDR_STORAGE',)
  ['HAVE_SOCKETPAIR', 'socketpair', '#include<sys/socket.h>'],
# check token ('HAVE_SSIZE_T',)
  ['HAVE_STATVFS', 'statvfs', '#include<sys/statvfs.h>'],
# check token ('HAVE_STAT_TV_NSEC',)
# check token ('HAVE_STAT_TV_NSEC2',)
# check token ('HAVE_STDARG_PROTOTYPES',)
# check token ('HAVE_STD_ATOMIC',)
  ['HAVE_STRDUP', 'strdup', '#include<string.h>'],
  ['HAVE_STRFTIME', 'strftime', '#include<time.h>'],
  ['HAVE_STRLCPY', 'strlcpy', '#include<string.h>'],
# check token ('HAVE_STRUCT_PASSWD_PW_GECOS',)
# check token ('HAVE_STRUCT_PASSWD_PW_PASSWD',)
# check token ('HAVE_STRUCT_STAT_ST_BIRTHTIME',)
# check token ('HAVE_STRUCT_STAT_ST_BLKSIZE',)
# check token ('HAVE_STRUCT_STAT_ST_BLOCKS',)
# check token ('HAVE_STRUCT_STAT_ST_FLAGS',)
# check token ('HAVE_STRUCT_STAT_ST_GEN',)
# check token ('HAVE_STRUCT_STAT_ST_RDEV',)
# check token ('HAVE_STRUCT_TM_TM_ZONE',)
  ['HAVE_SYMLINK', 'symlink', '#include<unistd.h>'],
  ['HAVE_SYMLINKAT', 'symlinkat', '#include<unistd.h>'],
  ['HAVE_SYNC', 'sync', '#include<unistd.h>'],
  ['HAVE_SYSCONF', 'sysconf', '#include<unistd.h>'],
  ['HAVE_TCGETPGRP', 'tcgetpgrp', '#include<unistd.h>'],
  ['HAVE_TCSETPGRP', 'tcsetpgrp', '#include<unistd.h>'],
  ['HAVE_TEMPNAM', 'tempnam', '#include<stdio.h>'],
  ['HAVE_TGAMMA', 'tgamma', '#include<math.h>'],
  ['HAVE_TIMEGM', 'timegm', '#include<time.h>'],
  ['HAVE_TIMES', 'times', '#include<sys/times.h>'],
# check token ('HAVE_TMPFILE',)
  ['HAVE_TMPNAM', 'tmpnam', '#include<stdio.h>'],
  ['HAVE_TMPNAM_R', 'tmpnam_r', '#include<stdio.h>'],
# check token ('HAVE_TM_ZONE',)
  ['HAVE_TRUNCATE', 'truncate', '#include<unistd.h>'],
  ['HAVE_TZNAME', 'tzname', '#include<time.h>'],
# check token ('HAVE_UCS4_TCL',)
  ['HAVE_UNAME', 'uname', '#include<sys/utsname.h>'],
  ['HAVE_UNLINKAT', 'unlinkat', '#include<unistd.h>'],
  ['HAVE_UNSETENV', 'unsetenv', '#include<stdlib.h>'],
# check token ('HAVE_USABLE_WCHAR_T',)
  ['HAVE_UTIMENSAT', 'utimensat', '#include<sys/stat.h>'],
  ['HAVE_UTIMES', 'utimes', '#include<sys/time.h>'],
  ['HAVE_WAIT3', 'wait3', '#include<sys/wait.h>'],
  ['HAVE_WAIT4', 'wait4', '#include<sys/wait.h>'],
  ['HAVE_WAITID', 'waitid', '#include<sys/wait.h>'],
  ['HAVE_WAITPID', 'waitpid', '#include<sys/wait.h>'],
# check token ('HAVE_WCSCOLL',)
# check token ('HAVE_WCSFTIME',)
# check token ('HAVE_WCSXFRM',)
  ['HAVE_WMEMCMP', 'wmemcmp', '#include<wchar.h>'],
# check token ('HAVE_WORKING_TZSET',)
  ['HAVE_WRITEV', 'writev', '#include<sys/uio.h>'],
# check token ('HAVE_ZLIB_COPY',)
# check token ('HAVE__GETPTY',)
]

foreach f : check_functions
  if cc.has_function(f.get(1), prefix : f.get(2), args : ['-D_POSIX_C_SOURCE=200809L', '-D_GNU_SOURCE'])
    cdata.set(f.get(0), 1)
  endif
endforeach

cdata.set('SIZEOF_DOUBLE', cc.sizeof('double'))
cdata.set('SIZEOF_FLOAT', cc.sizeof('float'))
cdata.set('SIZEOF_FPOS_T', cc.sizeof('fpos_t'))
cdata.set('SIZEOF_INT', cc.sizeof('int'))
cdata.set('SIZEOF_LONG', cc.sizeof('long'))
cdata.set('SIZEOF_LONG_DOUBLE', cc.sizeof('long double'))
cdata.set('SIZEOF_LONG_LONG', cc.sizeof('long long'))
cdata.set('SIZEOF_OFF_T', cc.sizeof('off_t', prefix : '#include<sys/types.h>'))
cdata.set('SIZEOF_PID_T', cc.sizeof('pid_t', prefix : '#include<sys/types.h>'))
cdata.set('SIZEOF_PTHREAD_T', cc.sizeof('pthread_t', prefix : '#include<pthread.h>'))
cdata.set('SIZEOF_SHORT', cc.sizeof('short'))
cdata.set('SIZEOF_SIZE_T', cc.sizeof('size_t'))
cdata.set('SIZEOF_TIME_T', cc.sizeof('time_t', prefix : '#include<time.h>'))
cdata.set('SIZEOF_UINTPTR_T', cc.sizeof('uintptr_t', prefix : '#include<stdint.h>'))
cdata.set('SIZEOF_VOID_P', cc.sizeof('void*'))
cdata.set('SIZEOF_WCHAR_T', cc.sizeof('wchar_t', prefix : '#include<wchar.h>'))
#cdata.set('SIZEOF__BOOL', cc.sizeof('_bool'))

# These are set manually. They work on 64 bit Linux.
# I was too lazy to convert the actual tests.

cdata.set('HAVE_STDARG_PROTOTYPES', 1)
cdata.set('HAVE_LONG_LONG', 1)
cdata.set('HAVE_DLOPEN', 1)
cdata.set('_LARGEFILE_SOURCE', 1)
cdata.set('_GNU_SOURCE', 1)
cdata.set('_POSIX_C_SOURCE', '200809L')
cdata.set('_XOPEN_SOURCE', 700)
cdata.set('_XOPEN_SOURCE_EXTENDED', 1)
cdata.set('HAVE_STRUCT_TM_TM_ZONE', 1)
cdata.set('HAVE_TM_ZONE', 1)
cdata.set('TIME_WITH_SYS_TIME', 1)
cdata.set('WITH_THREAD', 1)
cdata.set('HAVE_DECL_RTLD_DEEPBIND', 1)
cdata.set('HAVE_DECL_RTLD_GLOBAL', 1)
cdata.set('HAVE_DECL_RTLD_LAZY', 1)
cdata.set('HAVE_DECL_RTLD_LOCAL', 1)
cdata.set('HAVE_DECL_RTLD_NODELETE', 1)
cdata.set('HAVE_DECL_RTLD_NOLOAD', 1)
cdata.set('HAVE_DECL_RTLD_NOW', 1)

configure_file(input : 'pyconfig.h.meson',
  output : 'pyconfig.h',
  configuration : cdata)

incs = include_directories('Include')

parser_src = ['Parser/acceler.c',
  'Parser/bitset.c',
  'Parser/firstsets.c',
  'Parser/grammar1.c',
  'Parser/grammar.c',
  'Parser/listnode.c',
  'Parser/metagrammar.c',
  'Parser/myreadline.c',
  'Parser/node.c',
  'Parser/parser.c',
  'Parser/parsetok.c',
  'Parser/parsetok_pgen.c',
  'Parser/pgen.c',
#  'Parser/pgenmain.c',
  'Parser/printgrammar.c',
  'Parser/tokenizer.c',
  'Parser/tokenizer_pgen.c',
]

python_src = ['Python/asdl.c',
  'Python/ast.c',
  'Python/bltinmodule.c',
  'Python/bootstrap_hash.c',
  'Python/ceval.c',
  'Python/codecs.c',
  'Python/compile.c',
  'Python/dtoa.c',
  'Python/dup2.c',
  'Python/dynamic_annotations.c',
#  'Python/dynload_aix.c',
#  'Python/dynload_dl.c',
#  'Python/dynload_hpux.c',
#  'Python/dynload_next.c',
  'Python/dynload_shlib.c',
#  'Python/dynload_stub.c',
#  'Python/dynload_win.c',
  'Python/errors.c',
  'Python/fileutils.c',
  'Python/formatter_unicode.c',
  'Python/frozen.c',
  'Python/frozenmain.c',
  'Python/future.c',
  'Python/getargs.c',
  'Python/getcompiler.c',
  'Python/getcopyright.c',
  'Python/getopt.c',
  'Python/getplatform.c',
  'Python/getversion.c',
  'Python/graminit.c',
  'Python/import.c',
  'Python/importdl.c',
  'Python/marshal.c',
  'Python/modsupport.c',
  'Python/mysnprintf.c',
  'Python/mystrtoul.c',
  'Python/peephole.c',
  'Python/pyarena.c',
  'Python/pyctype.c',
  'Python/pyfpe.c',
  'Python/pyhash.c',
  'Python/pylifecycle.c',
  'Python/pymath.c',
  'Python/pystate.c',
  'Python/pystrcmp.c',
  'Python/pystrhex.c',
  'Python/pystrtod.c',
  'Python/Python-ast.c',
  'Python/pythonrun.c',
  'Python/pytime.c',
#  'Python/strdup.c',
  'Python/structmember.c',
  'Python/symtable.c',
  'Python/sysmodule.c',
  'Python/thread.c',
  'Python/traceback.c',
  'Python/_warnings.c',
]

object_src = ['Objects/abstract.c',
  'Objects/accu.c',
  'Objects/boolobject.c',
  'Objects/bytearrayobject.c',
  'Objects/bytes_methods.c',
  'Objects/bytesobject.c',
  'Objects/call.c',
  'Objects/capsule.c',
  'Objects/cellobject.c',
  'Objects/classobject.c',
  'Objects/codeobject.c',
  'Objects/complexobject.c',
  'Objects/descrobject.c',
  'Objects/dictobject.c',
  'Objects/enumobject.c',
  'Objects/exceptions.c',
  'Objects/fileobject.c',
  'Objects/floatobject.c',
  'Objects/frameobject.c',
  'Objects/funcobject.c',
  'Objects/genobject.c',
  'Objects/iterobject.c',
  'Objects/listobject.c',
  'Objects/longobject.c',
  'Objects/memoryobject.c',
  'Objects/methodobject.c',
  'Objects/moduleobject.c',
  'Objects/namespaceobject.c',
  'Objects/object.c',
  'Objects/obmalloc.c',
  'Objects/odictobject.c',
  'Objects/rangeobject.c',
  'Objects/setobject.c',
  'Objects/sliceobject.c',
  'Objects/structseq.c',
  'Objects/tupleobject.c',
  'Objects/typeobject.c',
  'Objects/unicodectype.c',
  'Objects/unicodeobject.c',
  'Objects/weakrefobject.c',
]

module_src = ['Modules/gcmodule.c',
  'Modules/getpath.c',
  'Modules/hashtable.c',
  'Modules/getbuildinfo.c',
  'Modules/signalmodule.c',
  'Modules/_tracemalloc.c',
  'Modules/faulthandler.c',
  'Modules/config.c', # FIXME, should be generated from the .in file.
  'Modules/main.c',
  'Modules/atexitmodule.c',
  'Modules/posixmodule.c',
  'Modules/timemodule.c',
  'Modules/zipimport.c',
  'Modules/_codecsmodule.c',
  'Modules/_threadmodule.c',
  'Modules/itertoolsmodule.c',
  'Modules/symtablemodule.c',
  'Modules/errnomodule.c',
  'Modules/_stat.c',
  'Modules/_weakref.c',
  'Modules/_localemodule.c',
  'Modules/pwdmodule.c',
  'Modules/_functoolsmodule.c',
  'Modules/_operator.c',
  'Modules/_collectionsmodule.c',
  'Modules/xxsubtype.c',
  'Modules/_sre.c',
  'Modules/_io/iobase.c',
  'Modules/_io/_iomodule.c',
  'Modules/_io/bufferedio.c',
  'Modules/_io/fileio.c',
  'Modules/_io/textio.c',
  'Modules/_io/stringio.c',
  'Modules/_io/bytesio.c',
]

extra_defs = ['-DPYTHONPATH=":"',
  '-DPREFIX="/usr/local"',
  '-DEXEC_PREFIX="/usr/local"',
  '-DVERSION="3.7"',
  '-DVPATH=""',
]

pylib = static_library('pylib',
  parser_src, python_src, object_src, module_src,
  c_args : ['-DPy_BUILD_CORE', '-DSOABI="64"'] + extra_defs,
  include_directories : incs,
  dependencies : thread_dep)

pyexe = executable('python', 'Programs/python.c',
  include_directories : incs,
  link_with : pylib,
  dependencies : [thread_dep, m_dep])



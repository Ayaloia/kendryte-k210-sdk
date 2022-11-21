from building import *

cwd     = GetCurrentDir()
src     = Split('''
lib/bsp/entry.c
lib/bsp/entry_user.c
lib/drivers/aes.c
lib/drivers/clint.c
lib/drivers/dmac.c
lib/drivers/dvp.c
lib/drivers/fft.c
lib/drivers/fpioa.c
lib/drivers/gpio.c
lib/drivers/gpiohs.c
lib/drivers/i2c.c
lib/drivers/i2s.c
lib/drivers/kpu.c
lib/drivers/plic.c
lib/drivers/pwm.c
lib/drivers/rtc.c
lib/drivers/sha256.c
lib/drivers/spi.c
lib/drivers/sysctl.c
lib/drivers/timer.c
lib/drivers/utils.c
lib/drivers/wdt.c
lib/nncase/v0/runtime/kernel_registry.cpp
lib/nncase/v0/runtime/interpreter.cpp
lib/nncase/v0/runtime/neutral/neutral_ops.cpp
lib/nncase/v0/runtime/k210/interpreter.cpp
lib/nncase/v0/runtime/k210/k210_ops.cpp
lib/nncase/v0/runtime/cpu/cpu_ops.cpp
lib/nncase/nncase.cpp

lib/nncase/v0/nncase_v0.cpp
lib/nncase/v1/nncase_v1.cpp

lib/bsp/sleep.c
''')
CPPPATH = [cwd + '/lib/drivers/include',
cwd + '/lib/nncase/v0/include',
cwd + '/lib/nncase/include',
cwd + '/third_party/xtl/include',
cwd + '/lib/bsp/include',
cwd + '/lib/utils/include',

cwd + '/lib/nncase/v0',
cwd + '/lib/nncase/v1',
cwd + '/lib/nncase/v1/include',
cwd + '/third_party/gsl-lite/include',
cwd + '/third_party/mpark-variant/include'
]
CPPDEFINES = ['NNCASE_TARGET=k210',
'TCB_SPAN_NO_EXCEPTIONS',
'TCB_SPAN_NO_CONTRACT_CHECKING',
'LV_CONF_INCLUDE_SIMPLE', 
'_IOMEM_MALLOC_H', 
'iomem_malloc=malloc', 
'iomem_free=free', 
'CONFIG_LOG_COLORS', 
'CONFIG_LOG_ENABLE', 
'CONFIG_LOG_LEVEL=LOG_VERBOSE', 
'FPGA_PLL', 
'LOG_KERNEL', 
'__riscv64']

LIBPATH = [
cwd + '/lib/nncase/v1/lib'
]

LIBS = [
'nncase.runtime',
'nncase.rt_modules.k210'
]
#这个顺序有先后……

group = DefineGroup('K210-SDK', src, depend = ['PKG_USING_K210_SDK'], CPPPATH = CPPPATH, LOCAL_CPPDEFINES = CPPDEFINES , LIBS=LIBS, LIBPATH = LIBPATH)

Return('group')

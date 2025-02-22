import rtconfig
from building import *

# get current directory
cwd = GetCurrentDir()

# The set of source files associated with this SConscript file.

CPPDEFINES = []

sdk_path = os.path.join(cwd, "EVT", "EXAM", "SRC")
patch_path = os.path.join(cwd, "rtt-patch")

src = Glob(os.path.join(sdk_path, "Core", "*.c")) + \
    Glob(os.path.join(sdk_path, "Peripheral", "src", "*.c")) + \
    Glob(os.path.join(patch_path, "*.c"))

path = [
    os.path.join(sdk_path, "Core"),
    os.path.join(sdk_path, "Peripheral", "inc"),
    patch_path
]

if GetDepend(['SOC_RISCV_SERIES_CH32V20x_D6']):
    print("CH32V20x_D6 is not supported yet.")
    src += Glob(os.path.join(patch_path, "startup_ch32v20x_D6.S"))
    CPPDEFINES.append("CH32V20x_D6")
    Exit()
elif GetDepend(['SOC_RISCV_SERIES_CH32V20x_D8']):
    print("CH32V20x_D8 is not supported yet.")
    src += Glob(os.path.join(patch_path, "startup_ch32v20x_D8.S"))
    CPPDEFINES.append("CH32V20x_D8")
    Exit()
elif GetDepend(['SOC_RISCV_SERIES_CH32V20x_D8W']):
    src += Glob(os.path.join(patch_path, "startup_ch32v20x_D8W.S"))
    CPPDEFINES.append("CH32V20x_D8W")


group = DefineGroup(
    'Libraries',
    src,
    depend=['PKG_USING_CH32V20x_SDK'],
    CPPPATH=path,
    CPPDEFINES=CPPDEFINES,
)

# TODO BLE lib is under `EVT/EXAM/BLE`, not support yet.

Return('group')

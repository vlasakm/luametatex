project(
  'luametatex',
  'c',
  version: '2.10',
  default_options: [
    'c_std=gnu11',
    'default_library=static',
  ],
)

cflags = [
  #'-fgnu89-inline',
]

cc = meson.get_compiler('c')

add_project_arguments(
  cc.get_supported_arguments(cflags),
  language: 'c',
)

lua_src = files(
  'source/luacore/lua54/src/lapi.c',
  'source/luacore/lua54/src/lauxlib.c',
  'source/luacore/lua54/src/lbaselib.c',
  'source/luacore/lua54/src/lcode.c',
  'source/luacore/lua54/src/lcorolib.c',
  'source/luacore/lua54/src/lctype.c',
  'source/luacore/lua54/src/ldblib.c',
  'source/luacore/lua54/src/ldebug.c',
  'source/luacore/lua54/src/ldo.c',
  'source/luacore/lua54/src/ldump.c',
  'source/luacore/lua54/src/lfunc.c',
  'source/luacore/lua54/src/lgc.c',
  'source/luacore/lua54/src/linit.c',
  'source/luacore/lua54/src/liolib.c',
  'source/luacore/lua54/src/llex.c',
  'source/luacore/lua54/src/lmathlib.c',
  'source/luacore/lua54/src/lmem.c',
  'source/luacore/lua54/src/loadlib.c',
  'source/luacore/lua54/src/lobject.c',
  'source/luacore/lua54/src/lopcodes.c',
  'source/luacore/lua54/src/loslib.c',
  'source/luacore/lua54/src/lparser.c',
  'source/luacore/lua54/src/lstate.c',
  'source/luacore/lua54/src/lstring.c',
  'source/luacore/lua54/src/lstrlib.c',
  'source/luacore/lua54/src/ltable.c',
  'source/luacore/lua54/src/ltablib.c',
  'source/luacore/lua54/src/ltm.c',
  'source/luacore/lua54/src/lua.c',
  'source/luacore/lua54/src/lundump.c',
  'source/luacore/lua54/src/lutf8lib.c',
  'source/luacore/lua54/src/lvm.c',
  'source/luacore/lua54/src/lzio.c',

  'source/luacore/luapeg/lptree.c',
  'source/luacore/luapeg/lpvm.c',
  'source/luacore/luapeg/lpprint.c',
  'source/luacore/luapeg/lpcap.c',
  'source/luacore/luapeg/lpcset.c',
  'source/luacore/luapeg/lpcode.c',
)

lua_c_args = [
  '-DLUAI_MAXCSTACK=6000',
  '-DLUA_UCID', # permits utf8 
  '-DLPEG_DEBUG',
  '-DLUA_NOBUILTIN', # disable likely usage
  '-DNDEBUG=0',
]

lua_inc = include_directories(
  'source/luacore/lua54/src',
  'source/luacore/luapeg',
)

lua_lib = library(
  'lua',
  sources: lua_src,
  include_directories: lua_inc,
  c_args: lua_c_args,
  override_options : ['c_std=c11'],
)

lua_dep = declare_dependency(
  link_with: lua_lib,
  include_directories: lua_inc,
  compile_args: lua_c_args,
)

luaoptional_src = files(
  'source/luaoptional/lmtsqlite.c',
  'source/luaoptional/lmtmysql.c',
  'source/luaoptional/lmtpostgress.c',
  'source/luaoptional/lmtcurl.c',
  'source/luaoptional/lmtghostscript.c',
  'source/luaoptional/lmtimagemagick.c',
  'source/luaoptional/lmtgraphicsmagick.c',
  'source/luaoptional/lmtzint.c',
  'source/luaoptional/lmtmujs.c',
  'source/luaoptional/lmtlzo.c',
  'source/luaoptional/lmtlz4.c',
  'source/luaoptional/lmtkpse.c',
  'source/luaoptional/lmthb.c',
  'source/luaoptional/lmtzstd.c',
  'source/luaoptional/lmtlzma.c',
  'source/luaoptional/lmtforeign.c',
)

luaoptional_inc = include_directories(
  '.',
  'source/.',
  'source/luacore/lua54/src',
  'source/libraries/mimalloc/include',
)

luaoptional_lib = library(
  'luaoptional',
  sources: luaoptional_src,
  include_directories: luaoptional_inc,
)

luarest_src = files(
  'source/luaoptional/lmtcerflib.c',

  'source/libraries/libcerf/erfcx.c',
  'source/libraries/libcerf/err_fcts.c',
  'source/libraries/libcerf/im_w_of_x.c',
  'source/libraries/libcerf/w_of_z.c',
  'source/libraries/libcerf/width.c',
)

luarest_inc = include_directories(
  'source/libraries/libcerf',
  'source/luacore/lua54/src',
  'source',
)

luarest_lib = library(
  'luarest',
  sources: luarest_src,
  include_directories: luarest_inc,
)

luasocket_src = files(
  'source/luacore/luasocket/src/auxiliar.c',
  'source/luacore/luasocket/src/buffer.c',
  'source/luacore/luasocket/src/compat.c',
  'source/luacore/luasocket/src/except.c',
  'source/luacore/luasocket/src/inet.c',
  'source/luacore/luasocket/src/io.c',
  'source/luacore/luasocket/src/luasocket.c',
  'source/luacore/luasocket/src/mime.c',
  'source/luacore/luasocket/src/options.c',
  'source/luacore/luasocket/src/select.c',
  'source/luacore/luasocket/src/socket.c',
  'source/luacore/luasocket/src/tcp.c',
  'source/luacore/luasocket/src/timeout.c',
  'source/luacore/luasocket/src/udp.c',
)

luasocket_inc = include_directories(
  'source/luacore/luasocket',
  'source/luacore/lua54/src',
)

luasocket_lib = library(
  'luasocket',
  sources: luasocket_src,
  include_directories: luasocket_inc,
)

miniz_src = files(
  'source/libraries/miniz/miniz.c',
)

miniz_c_args = [
  '-DMINIZ_NO_ARCHIVE_APIS=1',
  '-DMINIZ_NO_STDIO=1',
  '-DMINIZ_NO_MALLOC=1',
]

miniz_lib = library(
  'miniz',
  sources: miniz_src,
  c_args: lua_c_args,
)

mp_src = files(
  'source/mp/mpc/mp.c',
  'source/mp/mpc/mpstrings.c',
  'source/mp/mpc/mpmath.c',
  'source/mp/mpc/mpmathdouble.c',
  'source/mp/mpc/mpmathbinary.c',
  'source/mp/mpc/mpmathdecimal.c',
  'source/mp/mpc/mpmathposit.c',

  'source/libraries/decnumber/decContext.c',
  'source/libraries/decnumber/decNumber.c',

  'source/libraries/avl/avl.c',

  'source/lua/lmtmplib.c',

  'source/luarest/lmtxdecimallib.c',
)

mp_inc = include_directories(
  '.',
  'source/.',
  'source/mp/mpc',
  'source/luacore/lua54/src',
  'source/libraries/avl',
  'source/libraries/decnumber',
  'source/utilities',
  'source/libraries/mimalloc/include',
  'source/libraries/softposit/source/include',
)

mp_c_args = [
  '-DDECUSE64=1',
  '-DDECNUMDIGITS=1000',
]

mp_lib = library(
  'mp',
  sources: mp_src,
  include_directories: mp_inc,
  c_args: mp_c_args,
)

potrace_src = files(
  'source/libraries/potrace/src/potracelib.c',
  'source/libraries/potrace/src/curve.c',
  'source/libraries/potrace/src/decompose.c',
  'source/libraries/potrace/src/trace.c',
)

potrace_inc = include_directories(
  'source/libraries/mimalloc/include',
  'source/libraries/potrace/src',
)

potrace_c_args = [
  '-DVERSION="1.16"',
]

potrace_lib = library(
  'potrace',
  sources: potrace_src,
  include_directories: potrace_inc,
  c_args: potrace_c_args,
)

pplib_src = files(
  'source/libraries/pplib/pparray.c',
  'source/libraries/pplib/ppcrypt.c',
  'source/libraries/pplib/ppdict.c',
  'source/libraries/pplib/ppheap.c',
  'source/libraries/pplib/ppload.c',
  'source/libraries/pplib/ppstream.c',
  'source/libraries/pplib/ppxref.c',
  'source/libraries/pplib/util/utilbasexx.c',
  'source/libraries/pplib/util/utilcrypt.c',
  'source/libraries/pplib/util/utilflate.c',
  'source/libraries/pplib/util/utilfpred.c',
  'source/libraries/pplib/util/utiliof.c',
  'source/libraries/pplib/util/utillog.c',
  'source/libraries/pplib/util/utillzw.c',
  'source/libraries/pplib/util/utilmd5.c',
  'source/libraries/pplib/util/utilmem.c',
  'source/libraries/pplib/util/utilmemheap.c',
  'source/libraries/pplib/util/utilmemheapiof.c',
  'source/libraries/pplib/util/utilmeminfo.c',
  'source/libraries/pplib/util/utilnumber.c',
  'source/libraries/pplib/util/utilsha.c',
)

pplib_inc = include_directories(
  'source/libraries/pplib',
  'source/libraries/pplib/util',

  'source/libraries/miniz',
)

pplib_lib = library(
  'pplib',
  sources: pplib_src,
  include_directories: pplib_inc,
)

softposit_src = files(
  'source/libraries/softposit/source/s_addMagsP32.c',
  'source/libraries/softposit/source/s_subMagsP32.c',
  'source/libraries/softposit/source/s_mulAddP32.c',
  'source/libraries/softposit/source/p32_to_ui32.c',
  'source/libraries/softposit/source/p32_to_ui64.c',
  'source/libraries/softposit/source/p32_to_i32.c',
  'source/libraries/softposit/source/p32_to_i64.c',
  'source/libraries/softposit/source/p32_roundToInt.c',
  'source/libraries/softposit/source/p32_add.c',
  'source/libraries/softposit/source/p32_sub.c',
  'source/libraries/softposit/source/p32_mul.c',
  'source/libraries/softposit/source/p32_mulAdd.c',
  'source/libraries/softposit/source/p32_div.c',
  'source/libraries/softposit/source/p32_eq.c',
  'source/libraries/softposit/source/p32_le.c',
  'source/libraries/softposit/source/p32_lt.c',
  'source/libraries/softposit/source/p32_sqrt.c',
  'source/libraries/softposit/source/ui32_to_p32.c',
  'source/libraries/softposit/source/ui64_to_p32.c',
  'source/libraries/softposit/source/i32_to_p32.c',
  'source/libraries/softposit/source/i64_to_p32.c',
  'source/libraries/softposit/source/s_approxRecipSqrt_1Ks.c',
  'source/libraries/softposit/source/c_convertDecToPosit32.c',
  'source/libraries/softposit/source/c_convertPosit32ToDec.c',
  'source/libraries/softposit/source/c_int.c',
)

softposit_inc = include_directories(
  'source/libraries/softposit/source',
  'source/libraries/softposit/source/include',
  'source/libraries/softposit/build/Linux-x86_64-GCC',
)

softposit_c_args = [
  '-DSOFTPOSIT_FAST_INT64',
]

softposit_lib = library(
  'softposit',
  sources: softposit_src,
  include_directories: softposit_inc,
  c_args: softposit_c_args,
)

tex_src = files(
  'source/utilities/auxmemory.c',
  'source/utilities/auxzlib.c',
  'source/utilities/auxsparsearray.c',
  'source/utilities/auxsystem.c',
  'source/utilities/auxunistring.c',
  'source/utilities/auxfile.c',
  'source/utilities/auxposit.c',

  'source/libraries/hnj/hnjhyphen.c',

  'source/lua/lmtinterface.c',
  'source/lua/lmtlibrary.c',
  'source/lua/lmtcallbacklib.c',
  'source/lua/lmtlanguagelib.c',
  'source/lua/lmtlualib.c',
  'source/lua/lmtluaclib.c',
  'source/lua/lmttexiolib.c',
  'source/lua/lmttexlib.c',
  'source/lua/lmttokenlib.c',
  'source/lua/lmtnodelib.c',
  'source/lua/lmtenginelib.c',
  'source/lua/lmtfontlib.c',
  'source/lua/lmtstatuslib.c',

  'source/luaoptional/lmtoptional.c',

  'source/luarest/lmtfilelib.c',
  'source/luarest/lmtpdfelib.c',
  'source/luarest/lmtiolibext.c',
  'source/luarest/lmtoslibext.c',
  'source/luarest/lmtstrlibext.c',
  'source/luarest/lmtdecodelib.c',
  'source/luarest/lmtsha2lib.c',
  'source/luarest/lmtmd5lib.c',
  'source/luarest/lmtaeslib.c',
  'source/luarest/lmtbasexxlib.c',
  'source/luarest/lmtxmathlib.c',
  'source/luarest/lmtxcomplexlib.c',
  'source/luarest/lmtziplib.c',
  'source/luarest/lmtsparselib.c',
  'source/luarest/lmtposit.c',
  'source/luarest/lmtpotrace.c',

  'source/tex/texalign.c',
  'source/tex/texarithmetic.c',
  'source/tex/texbuildpage.c',
  'source/tex/texcommands.c',
  'source/tex/texconditional.c',
  'source/tex/texdirections.c',
  'source/tex/texdumpdata.c',
  'source/tex/texequivalents.c',
  'source/tex/texerrors.c',
  'source/tex/texexpand.c',
  'source/tex/texmarks.c',
  'source/tex/texinputstack.c',
  'source/tex/texinserts.c',
  'source/tex/texadjust.c',
  'source/tex/texlinebreak.c',
  'source/tex/texlocalboxes.c',
  'source/tex/texmainbody.c',
  'source/tex/texmaincontrol.c',
  'source/tex/texmathcodes.c',
  'source/tex/texmlist.c',
  'source/tex/texnesting.c',
  'source/tex/texpackaging.c',
  'source/tex/texprimitive.c',
  'source/tex/texprinting.c',
  'source/tex/texscanning.c',
  'source/tex/texstringpool.c',
  'source/tex/textypes.c',
  'source/tex/texfont.c',
  'source/tex/texlanguage.c',
  'source/tex/texfileio.c',
  'source/tex/texmath.c',
  'source/tex/texnodes.c',
  'source/tex/textextcodes.c',
  'source/tex/textoken.c',
  'source/tex/texrules.c',
)

tex_inc = include_directories(
  '.',
  'source/.',
  'source/libraries/miniz',
  'source/libraries/pplib',
  'source/libraries/pplib/util',
  'source/luacore/lua54/src',
  'source/libraries/mimalloc/include',
  'source/libraries/softposit/source/include',
  'source/libraries/potrace/src',
)

tex_c_args = [
  '-DZLIB_CONST=1',
  '-DMINIZ_NO_ARCHIVE_APIS=1',
  '-DMINIZ_NO_STDIO=1',
  '-DMINIZ_NO_MALLOC=1',
]

tex_lib = library(
  'tex',
  sources: tex_src,
  include_directories: tex_inc,
  c_args: tex_c_args,
)


luametatex_src = files(
  'source/luametatex.c',
)

luametatex_inc = include_directories(
  '.',
  'source/.',
  'source/luacore/lua54/src',
)

luametatex_c_args = [
]

luametatex_libs = [
  tex_lib,
  lua_lib,
  mp_lib,

  luarest_lib,
  luasocket_lib,
  luaoptional_lib,

  pplib_lib,
  miniz_lib,
  softposit_lib,
  potrace_lib
]

luametatex_deps = [
  cc.find_library('m', required: false),
]

luametatex_exe = executable(
  'luametatex',
  sources: luametatex_src,
  include_directories: luametatex_inc,
  c_args: luametatex_c_args,
  link_with: luametatex_libs,
  dependencies: luametatex_deps,
)

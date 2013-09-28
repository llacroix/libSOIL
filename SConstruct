env = Environment(
        CC="clang",
        CFLAGS = "-arch i386 -arch x86_64", 
        LINKFLAGS = "-arch i386 -arch x86_64 -framework OpenGL -framework CoreFoundation",
        LDFLAGS="-framework OpenGL -framework CoreFoundation")


# Get our configuration options:
opts = Variables('wm.conf') # Change wm to the name of your app
opts.Add(PathVariable('PREFIX', 'Directory to install under', '/usr', PathVariable.PathIsDir))
opts.Update(env)
opts.Save('wm.conf', env) # Save, so user doesn't have to 

Help(opts.GenerateHelpText(env))

idir_prefix = '$PREFIX'
idir_lib    = '$PREFIX/lib'
idir_bin    = '$PREFIX/bin'
idir_inc    = '$PREFIX/include/SOIL'
Export('env idir_prefix idir_lib idir_bin idir_inc')

soil_sources = Glob("src/*.c")
#libsoil = env.Library('libSOIL', soil_sources)

static_lib = env.StaticLibrary(target="SOIL", source=soil_sources)
shared_lib = env.SharedLibrary(target="SOIL", source=soil_sources)

env.Install(idir_lib, static_lib)
env.Install(idir_lib, shared_lib)
env.Install(idir_inc, Glob('src/*.h'))

env.Alias('install', idir_prefix)

Default(static_lib, shared_lib)

env = Environment(
        CC="clang",
        CFLAGS = "-arch i386 -arch x86_64", 
        LINKFLAGS = "-arch i386 -arch x86_64 -framework OpenGL -framework CoreFoundation",
        LDFLAGS="-framework OpenGL -framework CoreFoundation")

soil_sources = Glob("src/*.c")
#libsoil = env.Library('libSOIL', soil_sources)

static_Lib = env.StaticLibrary(target="SOIL", source=soil_sources)
shared_lib = env.SharedLibrary(target="SOIL", source=soil_sources)

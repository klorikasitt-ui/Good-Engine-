# Good Engine 🎮

**Godot benzeri, Android oyun motoru**

Good Engine, su içmek kadar kolay bir şekilde oyun geliştirmeyi sağlayan, açık kaynaklı ve GPL v3 lisansı ile korunan bir oyun motorudur.

## 🌟 Özellikler

- **Kolay Kullanım**: Su içmek kadar basit arayüz
- **Geniş Model Kütüphanesi**: Hazır modlar ve 3D/2D varlıklar
- **Hazır Fizik Motoru**: Yerçekimi, çarpışma, dinamikler
- **Android Desteği**: Native Android NDK ile yüksek performans
- **Çoklu Dil Desteği**: C, Python, Rust, Go, Brainfuck ve daha fazlası
- **Eklentilebilir Sistem**: Milyonlarca uygulama ve model desteklenebilir
- **Hazır Komponentler**: Sprite, Collider, Rigidbody, Sound vb.

## 📋 Proje Yapısı

```
Good Engine/
├── core/                      # C ile yazılmış motor çekirdeği
│   ├── game_loop.c
│   ├── memory_manager.c
│   ├── resource_manager.c
│   └── event_system.c
├── scripting/                 # Scripting sistemleri
│   ├── python/                # Python bridge
│   ├── rust/                  # Rust FFI
│   ├── go/                    # Go bindings
│   ├── brainfuck/             # Brainfuck interpreter
│   └── common/                # Ortak arayüzler
├── graphics/                  # Grafik sistemi (Vulkan/OpenGL ES)
│   ├── renderer.c
│   ├── shader_compiler.c
│   └── texture_loader.c
├── physics/                   # Fizik motoru (Bullet/Rapier)
│   ├── physics_world.c
│   ├── rigidbody.c
│   └── collider.c
├── plugins/                   # Plugin sistemi
│   ├── plugin_loader.c
│   ├── plugin_interface.h
│   └── examples/
├── tools/                     # Geliştirici araçları
│   ├── editor/
│   ├── asset_tools/
│   └── build_tools/
├── assets/                    # Varsayılan varlık kütüphanesi
│   ├── models/
│   ├── textures/
│   ├── sounds/
│   └── prefabs/
├── tests/                     # Test dosyaları
├── docs/                      # Dokümantasyon
├── CMakeLists.txt            # Build konfigürasyonu
├── build.gradle              # Android build
└── LICENSE                   # GPL v3 Lisansı
```

## 🚀 Kurulum & Build

### Gereksinimler
- Android NDK 21+
- CMake 3.16+
- C Compiler (GCC/Clang)
- Python 3.8+ (opsiyonel)
- Rust 1.56+ (opsiyonel)
- Go 1.16+ (opsiyonel)

### Build (Android)
```bash
mkdir build
cd build
cmake .. -DANDROID_PLATFORM=android-28 -DCMAKE_TOOLCHAIN_FILE=$ANDROID_NDK/build/cmake/android.cmake
make
```

### Build (Development/Desktop)
```bash
mkdir build
cd build
cmake ..
make
./good_engine_test
```

## 📚 Hızlı Başlangıç

### 1. Basit Oyun Oluştur (C)
```c
#include "good_engine.h"

int main() {
    GameEngine *engine = ge_create_engine();
    Scene *scene = ge_create_scene("MainScene");
    
    // Oyuncu objesi ekle
    GameObject *player = ge_create_object("Player", scene);
    ge_add_component(player, "Sprite", "assets/player.png");
    ge_add_component(player, "Collider", "circle");
    ge_add_component(player, "Rigidbody", 1.0f);
    
    // Motor başlat
    ge_run(engine, scene);
    
    return 0;
}
```

### 2. Python ile Scripting
```python
from good_engine import GameObject, Scene

scene = Scene("GameScene")
player = GameObject("Player", scene)
player.add_sprite("assets/player.png")
player.add_collider("box")
player.add_rigidbody(mass=1.0)

scene.add_object(player)
scene.play()
```

## 🔌 Plugin Geliştirme

Plugin API sayesinde kendi modüllerinizi ekleyebilirsiniz:

```c
// my_plugin.c
#include "plugin_interface.h"

void plugin_init(PluginManager *pm) {
    register_component("CustomComponent", custom_component_create);
}

void plugin_shutdown() {
    // Temizle
}
```

## 📖 Dokümantasyon

Detaylı dokümantasyon `docs/` klasöründe bulunur:
- `docs/API.md` - API referansı
- `docs/SCRIPTING.md` - Scripting rehberi
- `docs/PHYSICS.md` - Fizik motoru kullanımı
- `docs/PLUGINS.md` - Plugin geliştirme

## 🤝 Katkıda Bulunma

Good Engine gelişimine katkıda bulunabilirsiniz:

1. Fork edin
2. Feature branch oluşturun (`git checkout -b feature/AmazingFeature`)
3. Değişiklikleri commit edin (`git commit -m 'Add AmazingFeature'`)
4. Branch'e push yapın (`git push origin feature/AmazingFeature`)
5. Pull Request açın

## 📝 Lisans

Good Engine, GNU General Public License v3.0 ile korunmaktadır.
Daha fazla bilgi için `LICENSE` dosyasını okuyun.

## 🎯 Gelişim Haritası

- [ ] **Stage 1**: Core C engine + Python bridge
- [ ] **Stage 2**: Physics engine + Graphics
- [ ] **Stage 3**: GUI Editor + Rust/Go support
- [ ] **Stage 4**: Brainfuck + Plugin system
- [ ] **Stage 5**: Model library + Community mods

## 📞 İletişim

- 🐛 Hataları bildir: Issues sekmesini kullan
- 💬 Tartışmalar: Discussions sekmesinde
- 📧 E-posta: contact@goodengine.dev (kurulunca)

---

**Good Engine ile oyun geliştirmeye başla!** 🎮✨

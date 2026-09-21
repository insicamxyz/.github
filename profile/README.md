# İnsicam

İnsicam, mikroçekirdek mimarisini temel alan, özgür ve geliştirilebilir bir işletim sistemi projesidir. Amaç; çekirdek, temel sistem bileşenleri, kullanıcı alanı ve sürücüleri açık sınırlarla ayrılmış, incelenebilir ve farklı kullanım alanlarına uyarlanabilir bir sistem kurmaktır.

## Proje ilkeleri

- **Özgür yazılım:** Kaynak kodu incelenebilir, değiştirilebilir, kopyalanabilir ve yeniden dağıtılabilir.
- **Mikroçekirdek yaklaşımı:** Çekirdek yalnızca gerekli temel sorumlulukları taşır. Sürücüler, dosya sistemleri, ağ bileşenleri ve diğer servisler mümkün olduğunca kullanıcı alanında, ayrı süreçler olarak çalışır.
- **IPC ile ayrıştırma:** Sistem bileşenleri ve sürücüler, süreçler arası iletişim (IPC) aracılığıyla haberleşir. Bu ayrım, güvenilirlik, hata yalıtımı ve farklı lisans modelleri için teknik bir sınır sağlar.
- **Merkezi geliştirme, özgür çoğaltma:** İnsicam merkezi bir proje olarak yönetilir; isteyen herkes projeyi çatallayabilir, inceleyebilir ve kendi türevini üretebilir. Bununla birlikte, İnsicam'ın ana geliştirme merkezi, yönü ve topluluk koordinasyonu korunur.
- **Açık inceleme:** Açık kaynak projelerini, türevlerini ve farklı işletim sistemi tasarımlarını inceleyerek bilgi edinir, öğrendiklerimizi özgür yazılım yaklaşımıyla projeye taşırız.

## İşletim sistemi mimarileri

İşletim sistemi tasarımlarını tek bir kalıba indirgemiyoruz. Başlıca yaklaşımları karşılaştırmalı olarak ele alıyoruz:

- **Monolitik çekirdek:** Sürücüler, dosya sistemleri, ağ ve diğer servisler çekirdek alanında çalışır. Linux ve BSD ailesi bu yaklaşımın güçlü, üretimde kanıtlanmış örnekleridir. Performans ve doğrudan erişim avantajlarına karşılık çekirdek içindeki bir hata daha geniş etki yaratabilir.
- **Mikroçekirdek:** Çekirdek; zamanlama, adres alanları, temel bellek yönetimi, kesmeler ve IPC gibi en temel görevlerle sınırlıdır. Diğer servisler izole süreçler halinde çalışır. İnsicam'ın ana yönelimi budur. GNU Hurd, farklı bir tasarımla mikroçekirdek fikrinin önemli özgür yazılım örneklerindendir.
- **Hibrit çekirdek:** Mikroçekirdek ve monolitik tasarımın özelliklerini birleştirir; bazı servisler performans veya pratiklik nedeniyle çekirdek alanında kalabilir. Apple'ın Darwin/XNU sistemi ve Windows NT ailesi hibrit yaklaşım ile anılan başlıca örneklerdir.
- **Modüler ve unikernel yaklaşımları:** Modüler çekirdekler çalışma zamanında bileşen ekleyip çıkarabilir. Unikernel'ler ise tek bir uygulamaya özel, daraltılmış sistem imajları üretir. Bu yaklaşımlar İnsicam'ın bileşen sınırlarını ve dağıtım seçeneklerini değerlendirirken yararlanacağımız tasarım alanlarıdır.

### İncelenen sistemler

İnsicam; Linux, BSD ailesi (FreeBSD, OpenBSD, NetBSD ve diğerleri), GNU Hurd, macOS, Darwin, XNU ve Windows gibi sistemlerin mimarisini, lisanslarını, araç zincirlerini ve topluluk pratiklerini inceler. Ayrıca deneysel ve eğitim amaçlı işletim sistemleri de tasarım fikirleri bakımından değerlidir. Bu inceleme, kodu veya lisansı uygun olmayan içerikleri kopyalama amacı taşımaz; teknik bilgiyi ve özgür yazılım ile uyumlu yaklaşımları anlamaya yöneliktir.

## Lisans modeli

İnsicam'ın temel işletim sistemi bileşenleri, çekirdek ve mikroçekirdek altyapısı **GNU Affero General Public License v3.0 veya sonrası (AGPLv3-or-later)** ile lisanslanacaktır.

Sistem servisleri ve kullanıcı alanı için iki yönlü bir model hedefliyoruz:

1. Copyleft gerektiren özgür yazılım geliştirmeleri için **AGPLv3-or-later**.
2. Özel mülk kod, internet servisi ve permissive lisans gerektiren entegrasyonlar için uygun olduğu ölçüde **MIT, BSD, Apache-2.0, ISC** veya benzeri özgür/permissive lisanslar.

IPC üzerinden ayrı süreçler olarak çalışan sürücüler, teknik ve hukuki koşullara uygun olmak kaydıyla özel mülk yazılım olabilir. Örneğin, NVIDIA GPU sürücüsü gibi bir sürücü İnsicam çekirdeğine kapalı kaynak olarak bağlanmak yerine tanımlı IPC protokolleri üzerinden hizmet verebilir. Bu açıklama hukuki danışmanlık değildir; her bileşenin lisansı, kaynak kodu, bağlantı biçimi ve dağıtım şekli ayrıca değerlendirilmelidir.

## Başlangıç araç zinciri ve diller

İşletim sisteminin ilk aşamalarında GNU Assembler (GAS), C ve C++ başta olmak üzere donanıma yakın ve sistem programlama dilleri kullanılacaktır. Daha sonra uygun bileşenlerde başka diller de değerlendirilebilir. Seçim ölçütlerimiz şunlardır:

- derleyici, çalışma zamanı ve kütüphane lisanslarının copyleft veya permissive lisans modeliyle uyumlu olması,
- hedef mimarilerde yeterli kontrol ve öngörülebilirlik sağlaması,
- bakım, denetlenebilirlik ve uzun vadeli yeniden üretilebilirlik.

## Kod ve içerik depoları

İnsicam kaynak kodunu, teknik belgelerini ve topluluk içeriklerini aşağıdaki merkezlerde saklamayı planlar:

- [GitHub](https://github.com/insicamxyz)
- [Codeberg](https://codeberg.org/insicamxyz)
- [Masscollabs kaynak sunucusu](https://source.masscollabs.xyz/insicamxyz)

Bu merkezler arasında eşgüdüm sağlanabilir; her platformdaki güncel proje durumu ve katkı yönergeleri ilgili depo içinde duyurulur.

## Logo

Projenin public domain logosu olarak [Yeşil Mavi](https://openclipart.org/detail/330390/ye%C5%9Fil-mavi) görselini kullanıyoruz. Görselin kaynağı Openclipart'tır; kullanım ve yeniden dağıtımda kaynağın güncel public domain durumunu ayrıca kontrol etmek iyi bir uygulamadır.

## Katkı

Tasarım tartışmaları, kod, dokümantasyon, test, araç zinciri çalışmaları ve mimari incelemeler değerlidir. Katkı göndermeden önce ilgili depodaki lisans, katkı ve davranış kurallarını inceleyin.

İnsicam'ın hedefi yalnızca çalışan bir işletim sistemi üretmek değil; sınırları açık, öğrenilebilir, özgürce çatallanabilir ve uzun süre geliştirilebilir bir sistem topluluğu kurmaktır.

## License

Copyright (C) 2026-2027 PSD Authors

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.

# 222523222_Sule_Yucelbas_YMG_Project
# Kütüphane Otomasyon Sistemi
# Proje İçeriği ve Çözümlemeler:
Bu projede, bir kütüphane otomasyonu uygulamasının basit bir grafik ara yüzü oluşturulmaya çalışılmıştır. Uygulama kitap eklemek, kitap silmek, kitap aramak, kitap ödünç almak, kitap iade etmek gibi işlevleri yerine getirebilmektedir. Bu proje, nesneye yönelik programlama (OOP) prensiplerine uygun bir şekilde Python dilinde hazırlanmıştır. Projeye ait kod, iki sınıf olan LibrarySystem ve LibraryApplication sınıflarını içermektedir.
LibrarySystem sınıfı, veri tabanı bağlantısı ve veri tabanı işlemlerini gerçekleştiren metotları içerir. LibraryApplication sınıfı, Tkinter kullanarak bir kullanıcı ara yüzü oluşturur ve bu ara yüzdeki butonlara bağlı işlevleri gerçekleştirir. Aynı zamanda LibrarySystem sınıfını kullanarak kitap ekleme, kitap silme, kitap arama gibi işlemleri gerçekleştirir. Böylece yazılan kod, nesne yönelimli programlama prensiplerini takip eder ve sınıflar arasında ilişkiyi sağlar. Her sınıf, özel metotlar ve veri alanları içerir ve ilgili işlemleri gerçekleştirir. Ayrıca, sınıflar arasında mesajlaşma ve işbirliği de vardır. 
Admin olarak giriş yapıldığında, kitap ekleme, kitap silme, tüm kitapları görüntüleme gibi ek işlevler kullanılabilir hale gelir. Kullanıcı olarak giriş yapıldığında, kitap arama, kiralanan kitapları görüntüleme, kitap ödünç alma ve kitap iade etme gibi işlevler kullanılabilir hale gelir. Kodun çalışması için Tkinter ve sqlite3 modüllerinin kurulu olması gerekmektedir. Bu kodda kullanıcı rolü, admin şifresi (admin123) veya kurum ortak şifresi (555) ile doğrulanır.  Projeye ait use case diyagramı Şekil 1’de görülmektedir.
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/9ef1a09e-f3ac-4863-90b8-c777bf8d2f89)
# Şekil 1. Kütüphane Otomasyonu use case diyagramı
LibrarySystem sınıfı, kitapları veri tabanında yönetmek için gerekli olan işlevleri içerir. sqlite3 modülünü kullanarak library.db adında bir veri tabanı oluşturur ve kitapları bu veri tabanında saklar. LibraryApplication sınıfı, grafik ara yüzünü oluşturmak ve kullanıcının kitapları yönetmesine olanak sağlamak için tkinter modülünü kullanır. Kodu çalıştırdıktan sonra yapılan eklemeler ve çıkarmalarla SQLite3 veri tabanı programında oluşan books tablosu Şekil 2’de ve 3’te görülmektedir.
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/77962d55-08f3-4846-9bcb-7f5b35202d43)
# Şekil 2. Kütüphane Otomasyonu Database browser
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/a9c9c005-4954-4a88-9907-af7c87a3c8de)
# Şekil 3. Kütüphane Otomasyonu Database browserda açılmış books tablosu
Ara yüz, kitap eklemek, silmek, aramak, ödünç almak, iade etmek gibi işlemleri gerçekleştirebilen düğmeler ve metin giriş alanları içerir. Projeye ait kodda yer alan metotların açıklamaları şu şekildedir:
1.	__init__(self): LibrarySystem sınıfının yapıcı metodudur. SQLite veritabanı ile bağlantı kurar ve books adında bir tablo oluşturur.
2.	add_book(self, title, author): Bir kitabı veritabanına ekler. title ve author parametreleriyle kitap adı ve yazarını alır.
3.	delete_book(self, id): Verilen bir kitabın kaydını veritabanından siler. id parametresiyle kitap kimliğini alır.
4.	search_books(self, title): Verilen bir kitap adına göre kitapları arar ve bulunan kitapların listesini döndürür. Eğer title parametresi boş ise tüm kitapları döndürür.
5.	view_returned_books(self): Kiralık olmayan kitapların listesini döndürür.
6.	borrow_book(self, id): Bir kitabı ödünç alındı durumuna getirir. id parametresiyle kitap kimliğini alır.
7.	return_book(self, id): Bir kitabın ödünç alındı durumunu kiralık durumuna getirir. id parametresiyle kitap kimliğini alır.
8.	__init__(self, window): LibraryApplication sınıfının yapıcı metodudur. Arayüzün oluşturulduğu Tkinter penceresini ayarlar.
9.	add_book(self): Kitap ekleme işlemini gerçekleştirir. Giriş alanlarından kitap adı ve yazarını alır, library_system nesnesi üzerinden add_book metoduyla kitabı veritabanına ekler.
10.	delete_book(self): Seçili kitabı siler. Listbox'ta seçili kitabın kimliğini ve durumunu kontrol eder. Eğer kitap kiralandıysa silme işlemi gerçekleştirmez ve bir hata mesajı gösterir.
11.	search_books(self): Kitapları aramak için kullanılır. Giriş alanından kitap adını alır, library_system nesnesi üzerinden search_books metoduyla kitapları arar ve sonuçları Listbox'ta gösterir.
12.	view_returned_books(self): Kiralık olmayan kitapları görüntüler. library_system nesnesi üzerinden view_returned_books metoduyla kiralık olmayan kitapları alır ve sonuçları Listbox'ta gösterir.
13.	borrow_book(self): Kitap ödünç alma işlemini gerçekleştirir. Listbox'ta seçili kitabı alır, library_system nesnesi üzerinden borrow_book metoduyla kitabın durumunu değiştirir.
14.	borrow_book_button_clicked(self): Bu metot, "Kitap Ödünç Al" düğmesine tıklandığında çağrılır. Öncelikle, is_admin değişkenine bakarak kullanıcının yönetici mi yoksa normal kullanıcı mı olduğunu kontrol eder. Eğer kullanıcı yönetici ise, borrow_book metodu çağrılır. Yönetici değilse, kullanıcıdan bir parola istenir ve bu parola check_common_password metoduna gönderilir. Eğer parola doğru ise, borrow_book metodu çağrılır. Aksi takdirde kullanıcıya "Geçersiz Kurum Ortak Şifresi!" şeklinde bir hata mesajı gösterilir.
15.	return_book(self): Bu metot, "Kitap İade" düğmesine tıklandığında çağrılır. Öncelikle, kullanıcının yönetici olup olmadığını kontrol eder. Eğer yönetici ise, return_book metodu doğrudan çağrılır ve kitap iade edilir. Yönetici değilse, kullanıcıdan bir parola istenir ve bu parola check_common_password metoduyla kontrol edilir. Eğer parola doğru ise, return_book metodu çağrılır ve kitap iade edilir. Aksi takdirde kullanıcıya "Geçersiz Kurum Ortak Şifresi!" şeklinde bir hata mesajı gösterilir.
16.	view_all_books(self): Bu metot, "Tüm kitapları gör" düğmesine tıklandığında çağrılır. search_books metodu çağrılarak tüm kitaplar getirilir ve Listbox'a eklenir.
17.	admin_login(self): Bu metot, "Giriş Yap" düğmesine tıklandığında çağrılır. Kullanıcının girdiği parola, "admin123" ile karşılaştırılır. Eğer parola doğru ise, is_admin değişkeni True olarak ayarlanır ve yönetici girişi gerçekleşir. Düğme metni "Çıkış Yap" olarak değiştirilir ve admin_logout metodu çağrıldığında yönetici çıkışı yapılır.
18.	admin_logout: Bu metot, "Çıkış Yap" düğmesine tıklandığında çağrılır. is_admin değişkeni False olarak ayarlanır ve yönetici çıkışı gerçekleşir. Düğme metni "Giriş Yap" olarak değiştirilir ve admin_login metodu çağrıldığında yönetici girişi yapılır.
19.	refresh_book_list: Bu metot, kitap listesini güncellemek için kullanılır. Öncelikle Listbox temizlenir ve search_books metodu çağrılarak tüm kitaplar getirilir ve Listbox'a eklenir.
20.	refresh_book_ids(self) metodu, kitapların ID'lerini güncellemek için kullanılır. Bu metot, tüm kitapları sorgular ve her bir kitabın ID'sini index değeriyle günceller. Başlangıç değeri 1'den başlayarak kitapları sıralar ve her kitabın ID'sini günceller. Bu işlem, kitaplar silindiğinde veya yeni kitaplar eklediğimizde ID'lerin doğru bir şekilde sıralanmasını sağlar.
21.	perform_search(self): Bu metot, arama yapmak için kullanılır. title değişkenine girilen kitap adını alır ve search_books metodunu çağırarak ilgili kitapları bulur ve listeler.
22.	check_common_password(self, password): Bu metot, kurum ortak şifresini kontrol etmek için kullanılır. password parametresi olarak girilen şifreyi kontrol eder ve eşleşip eşleşmediğini döndürür. Şu anda kabul edilen şifre "555" olarak belirlenmiştir.
Kütüphane Otomasyonu projesine ait UML class diyagramı Şekil 4’de görülmektedir.
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/58520d99-10ff-4ac9-b3ad-94c6ae6f0ac2)
# Şekil 4. Kütüphane Otomasyonu UML class diyagramı
Hazırlamış olduğum kütüphane otomasyon programının bazı güçlü yanları aşağıda belirtilmiştir:
•	Sınıf tabanlı bir tasarıma sahiptir: Kod, sınıf tabanlı bir yaklaşımla düzenlenmiştir. LibrarySystem ve LibraryApplication sınıfları, kütüphane işlemlerini ve GUI arayüzünü yönetir. Bu, kodun daha düzenli ve sürdürülebilir olmasını sağlar.
•	SQLite veritabanı kullanımı: LibrarySystem sınıfı, SQLite veritabanını kullanarak kitapların depolanmasını ve işlenmesini sağlar. Bu, veri kalıcılığını sağlar ve verilerin kaybolmasını önler.
•	Tkinter kullanımı: LibraryApplication sınıfı, Tkinter kütüphanesini kullanarak basit bir GUI (grafik kullanıcı arayüzü) oluşturur. Bu, kullanıcıların kitap eklemesini, silmesini, aramasını ve ödünç almasını/iade etmesini sağlar.
•	Kullanıcı yetkilendirmesi: admin_login ve admin_logout yöntemleri, admin kullanıcısının giriş yapmasını ve çıkış yapmasını sağlar. Bu, sadece yetkilendirilmiş kullanıcıların kitapları silmesine ve eklemesine izin verir.
•	Veri girişi doğrulaması: borrow_book_button_clicked ve return_book yöntemleri, kurum ortak şifresinin doğruluğunu kontrol eder. Bu, sadece doğru şifreyi giren kullanıcıların kitapları ödünç almasına ve iade etmesine izin verir.
•	Kitap listesinin güncellenmesi: refresh_book_list ve refresh_book_ids yöntemleri, kitap listesini günceller ve kitapların ID'lerini sıralar. Bu, kullanıcıların herhangi bir değişiklik olduğunda güncel bir kitap listesi görmesini sağlar.
•	Hata mesajları: messagebox modülü kullanılarak hata mesajları gösterilir. Bu, kullanıcılara hatalı girişler veya işlemler hakkında geri bildirim sağlar.
Bu iyi yanlar, projeye ait kodun okunabilir, yönetilebilir ve kullanıcı dostu olmasını sağlamaktadır. Ayrıca, veri tabanı kullanımı ve doğrulama işlemleri gibi güvenlik önlemleri de mevcuttur. Projeye ait grafik ara yüzü Şekil 5’de görülmektedir.
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/54c33f4a-89e4-4a49-a10f-35e5f9f19f0f)
# Şekil 5. Kütüphane Otomasyonu grafik ara yüzü
Programda, messagebox modülü kullanılarak hata mesajları ve girişler gösterilir. Bu, kullanıcılara hatalı girişleri veya işlemleri hakkında geri bildirim sağlamaktadır. Aşağıda, kullanıcının hatalı girişleri sonucunda alınan hata mesajları gösterilmektedir. Şekil 6, hatalı kurum ortak şifresi girildiğinde karşılaşılan hata mesajıdır.
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/6533d1b2-3d09-4b6c-a02b-74c591b1dc8e)
# Şekil 6. Yanlış kurum ortak şifresi girişi sonucunda alınan hata mesajı
Şekil 7 hatalı admin şifresi girildiğinde karşılaşılan hata mesajıdır.
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/932a539f-2c13-454c-8383-83fbbbcc3a5a)
# Şekil 7. Yanlış admin şifresi girişi sonucunda alınan hata mesajı
Şekil 8, kiralanmış bir kitap admin tarafından silinmeye çalışıldığında karşılaşılan hata mesajıdır.
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/224f1755-7836-4652-b00b-0c1a407500b7)
# Şekil 8. Kiralanmış bir kitap admin tarafından silinmeye çalışıldığında karşılaşılan hata mesajı
Son olarak Şekil 9, ortak kullanıcı bir kitabı kiralamak veya iade etmek istediğinde karşılaştığı giriş mesajını göstermektedir.
# ![image](https://github.com/Iskenderun-Technical-University/222523222_Sule_Yucelbas_YMG_Projectt/assets/37442135/0c63849f-e56b-45b3-bdd7-1d83a78e19d5)
# Şekil 9. Ortak kullanıcı bir kitabı kiralamak veya iade etmek istediğinde karşılaştığı giriş mesajı



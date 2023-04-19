# SEO Link Oluşturucu (seflink)

Bu PHP fonksiyonu, URL'lerde SEO dostu bağlantılar oluşturmak için kullanılabilir. Türkçe karakterleri ve özel karakterleri ingilizce karakterlere dönüştürerek, gereksiz boşlukları temizleyerek ve boşlukları tire ile değiştirerek bir metni SEO uyumlu bir şekilde dönüştürebilirsiniz.

## Örnek Kullanım
```php
$text = "Örnek Seo Cümlesi";
echo seflink($text);
// Çıktı: ornek-seo-cumlesi
```

## Fonksiyon

Fonksiyonun kullanımı aşağıdaki gibidir:

```php
function seflink($text)
{
  $find = array('Ç', 'Ş', 'Ğ', 'Ü', 'İ', 'Ö', 'ç', 'ş', 'ğ', 'ü', 'ö', 'ı', '+', '#');
  $replace = array('c', 's', 'g', 'u', 'i', 'o', 'c', 's', 'g', 'u', 'o', 'i', 'plus', 'sharp');
  $text = strtolower(str_replace($find, $replace, $text));
  $text = preg_replace("@[^A-Za-z0-9\-_\.\+]@i", ' ', $text);
  $text = trim(preg_replace('/\s+/', ' ', $text));
  $text = str_replace(' ', '-', $text);
  return $text;
}
```

Fonksiyonu [Codeigniter Framework](https://github.com/codeigniter4/CodeIgniter4) helperı olarak kullanabilirsiniz.


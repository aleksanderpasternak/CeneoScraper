# CeneoScraper

## Kod produktu, o którym będą pobierane opinie
84514582

## Algorytm pobierania opinii o pojedynczym produkcie z serwisu Ceneo.pl

1. Wysłanie żądania dostępu do strony z opiniami o produkcie
2. Jeśli operacja zakończy się sukcesem, wyodrębnienie z kodu strony fragmentów odpowiadających odpowiadających poszczególnym opiniom
3. Dla każdej z opinii wydobycie z kodu HTML poszczególnych składowych i zapisanie ich w postaci złożonych struktur danych
4. Jeżeli istnieje kolejna strona z opiniami, przejście na tą stronę i powtórzenie dla niej kroków 1-4
5. Zapisane wszystkich opinii w bazie danych

## Struktura opinii w serwisie Ceneo.pl
|Składowa|Zmienna|Selektor|
|--------|-------|--------|
|Opinia|review|div.js_product-review|
|Identyfikator opinii|review_id|['data-entry-id']|
|Autor|author|span.user-post__author-name|
|Rekomendacja|recommendation|span.user-post__author-recomendation > em|
|Liczba gwiazdek|stars|span.user-post__score-count|
|Treść opinii|content|div.user-post__text|
|Listba zalet|pros|div.review-feature__item--positive|
|Listba wad|cons|div.review-feature__item--negative|
|Ile osób uznało opinię za przydatną|likes|span[id^='votes-yes']|
|Ile osób uznało opinię za nieprzydatna|dislikes|span[id^='votes-no']|
|Data wystawienia opinii|publish_date|span.user-post__published > time:nth-child(1)['datetime']|
|Data zakupu produktu|purchase_date|span.user-post__published > time:nth-child(1)['datetime']|
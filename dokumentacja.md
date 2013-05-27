# Dokumentacja

## Usługa sieciowa

## Wersja 1.0

  <dl>
    <dt>Autor:</dt>
      <dd>Dominik Tomaszuk, Uniwersytet w&nbsp;Białymstoku</dd>
  </dl>
  <dl>
    <dt>Edytorzy:</dt>
      <dd>Dominik Tomaszuk, Uniwersytet w&nbsp;Białymstoku</dd>
      <dd>Radosław Piliszek</dd>
  </dl>

Licencja dokumentu: [Creative Commons Uznanie Autorstwa – Na Tych Samych Warunkach](http://creativecommons.org/licenses/by-sa/3.0/deed.pl)

* * *

</div>

<section>

## Streszczenie

Dokument ten opisuje sposób obsługi żądań i&nbsp;odpowiedzi w protokole HTTP. Opisuje strukturę zawartości ciała odpowiedzi w&nbsp;formatach JSON, XML i&nbsp;Atom.

</section>

<section id="toc">

## Spis treści

*   [<span class="secno">1. </span>Wprowadzenie](#wprowadzenie)
*   [<span class="secno">2. </span>JSON](#json)
*   [<span class="secno">3. </span>XML](#xml)
*   [<span class="secno">4. </span>Atom](#atom)
*   [<span class="secno">5. </span>API REST](#api_rest)
*   [<span class="secno">A. </span>Bibliografia](#bibliografia)
*   [<span class="secno">B. </span>Podziekowania](#podziekowania)
</section>

<section id="wprowadzenie" class="informative">

## <span class="secno">1. </span>Wprowadzenie

_Ta sekcja jest nienormatywna_

Dokument ten opisuje sposób obsługi żądań i odpowiedzi w protokole HTTP [[HTTP](#HTTP)].
    Dokument opisuje format wymiany między klientem a serwerem aplikacji XYZ. Prezentowane są formaty:

*   JSON [[RFC4627](#RFC4627)]
*   XML [[XML](#XML)]
*   Atom [[RFC4287](#RFC4287)]
</section>

<section id="json">

## <span class="secno">2. </span>JSON

  Struktura dokumentu JSON została opisana w JSON Schema [[JSONS](#JSONS)].
    <pre>{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "title": "Schemat JSON",
    "type": "array",
    "items": {
        "title": "Sekcja",
        "type": "object",
        "properties": {
            "tytul": {
                "description": "Tytuł sekcji",
                "type": "string"
            },
            "tresc": {
                "description": "Treść sekcji",
        "type": "string",
        "minLength": 1
            },
            "data": {
                "description": "Data opublikowania sekcji",
        "type": "string",
                "maxLength": 19,
                "minLength": 19
            }
        },
        "required": ["tresc"]
    }
}
    </pre>
</section>

<section id="xml" class="informative">

## <span class="secno">3. </span>XML

_Ta sekcja jest nienormatywna_

  Struktura dokumentu XML została opisana w RELAX NG Compact [[RNC](#RNC)].
    <pre>start =
  element serwis {
    element sekcja {
      element tytul { text }?,
      element tresc { text },
      element data { xsd:dateTime }?
    }+
  }
    </pre>
</section>

<section id="atom" class="informative">

## <span class="secno">4. </span>Atom

_Ta sekcja jest nienormatywna_

  Struktura dokumentu Atom została opisana w [[RFC4287](#RNC)].
</section>

<section id="api_rest">

## <span class="secno">5. </span>API REST

Obsługiwane kody HTTP:

*   `200 OK`
*   `302 Found`
*   `400 Bad Request`
*   `404 Not Found`
*   `410 Gone`
*   `502 Bad Gateway`

Przykład błędu 404

  <pre>
{
    "blad": "Nieporawny serwis"
}
  </pre>

Przykład błędu 410

  <pre>
{
    "blad": "Wybierz serwis"
}
  </pre>

Obsługiwane nagłówki HTTP:

*   `Allow` - wskazuje obsługiwane metody (`GET` i `HEAD`)
*   `Pragma`, `Cache-Control`, `Expires` - odpowiadają za cache'owanie
*   `Content-Type` - wskazuje obsługiwany typ danych, obowiązkowo `application/json; charset=utf-8` oraz opcjonalnie `application/xml; charset=utf-8`
*   `Location` - wykorzystywany jest w kodzie `302`
</section>

<section id="bibliografia" class="appendix">

## <span class="secno">A. </span>Bibliografia

    <dl class="bibliography">
      <dt id="RFC4627">[RFC4627]</dt>
      <dd>D. Crockford. [<cite>The application/json Media Type for JavaScript Object Notation (JSON)</cite>](http://www.ietf.org/rfc/rfc4627.txt). 2006. RFC 4627. URL: [http://www.ietf.org/rfc/rfc4627.txt](http://www.ietf.org/rfc/rfc4627.txt)
      <dt id="XML">[XML]</dt>
      <dd>T. Bray, J. Paoli, C. M. Sperberg-McQueen, E.e Maler, F. Yergeau, D. Crockford. [<cite>Extensible Markup Language (XML) 1.0 (Fifth Edition)</cite>](http://www.w3.org/TR/xml/). 2008. URL: [http://www.w3.org/TR/xml/](http://www.w3.org/TR/xml/)
      <dt id="HTTP">[HTTP]</dt>
      <dd>R. Fielding, J. Gettys, J. Mogul, H. Frystyk, L. Masinter, P. Leach, T. Berners-Lee. [<cite>Hypertext Transfer Protocol -- HTTP/1.1</cite>](http://www.w3.org/TR/xml/). 1999. RFC 2616 URL: [http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)
      <dt id="JSONS">[JSONS]</dt>
      <dd>K. Zyp. [<cite>JSON Schema: interactive and non interactive validation</cite>](http://tools.ietf.org/id/draft-fge-json-schema-validation-00.txt). 2013. URL: [http://tools.ietf.org/id/draft-fge-json-schema-validation-00.txt](http://tools.ietf.org/id/draft-fge-json-schema-validation-00.txt)
      <dt id="RNC">[RNC]</dt>
      <dd>J. Clark. [<cite>RELAX NG Compact Syntax</cite>](http://relaxng.org/compact-20021121.html). 2002. URL: [http://relaxng.org/compact-20021121.html](http://relaxng.org/compact-20021121.html)
      <dt id="RFC4287">[RFC4287]</dt>
      <dd>M. Nottingham, R. Sayre. [<cite>The Atom Syndication Format</cite>](http://www.ietf.org/rfc/rfc4287.txt). 2005. RFC 4287. URL: [http://www.ietf.org/rfc/rfc4287.txt](http://www.ietf.org/rfc/rfc4287.txt)
    </dl>
</section>

<section id="podziekowania" class="appendix informative">

## <span class="secno">B. </span>Podziękowania

_Ta sekcja jest nienormatywna_

Autorzy kierują serdeczne podziękowania do Dyrekcji Instytutu Informatyki UwB, a&nbsp;szczególnie Pani Dr Anety Polewko-Klim za wsparcie tego projektu.

Autor dziękuje również wszystkim studentom z&nbsp;Informatycznego Koła Naukowego (IKN), w&nbsp;szczególności: (w&nbsp;kolejności alfabetycznej)

*   Artemowi Barysevich
*   Karolowi Borkowskiemu
*   Radosławowi Piliszkowi
*   Maciejowi Puchalskiemu
*   Arturowi Szymańskiemu
</section>

---
title: Regeln für Konvertierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], literals
- conversions with numeric literals [ODBC]
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: 89f846a3-001d-496a-9843-ac9c38dc1762
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3ecee500204303dfcbcd8e179b9cb9cb0a94bae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706098"
---
# <a name="rules-for-conversions"></a>Regeln für Konvertierungen
Die Regeln in diesem Abschnitt gelten für Konvertierungen, die im Zusammenhang mit numerischen Literalen. Für die Zwecke dieser Regeln ist werden die folgenden Begriffe definiert:  
  
-   *Store-Zuweisung:* beim Senden von Daten in eine Tabellenspalte in einer Datenbank. Dies geschieht bei Aufrufen von **SQLExecute**, **SQLExecDirect**, und **SQLSetPos**. Bei der Zuweisung von Speicher "Target" bezieht sich auf eine Datenbankspalte, und "Quelle" bezieht sich auf die Daten in die Anwendungspuffer.  
  
-   *Abrufen von Zuweisung:* beim Abrufen von Daten aus der Datenbank in die Anwendungspuffer. Dies geschieht bei Aufrufen von **SQLFetch**, **SQLGetData**, **SQLFetchScroll**, und **SQLSetPos**. Bei der Zuordnung abrufen "Target" bezieht sich auf den Anwendungspuffer, und "Quelle" bezieht sich auf die Datenbankspalte.  
  
-   *CS:* den Wert in der Zeichenquelle.  
  
-   *NT:* den Wert in das numerische Ziel.  
  
-   *NS:* den Wert in der numerischen Quelle.  
  
-   *CT:* den Wert in der Ziel-Zeichen.  
  
-   Genauigkeit eines genauen numerischen Literals: die Anzahl der Ziffern, die sie enthält.  
  
-   Die Skalierung eines genauen numerischen Literals: die Anzahl der Ziffern rechts vom Punkt Sie ausdrücklich oder konkludent.  
  
-   Die Genauigkeit von einem ungefähren numerischen Literal: die Genauigkeit der Mantisse.  
  
## <a name="character-source-to-numeric-target"></a>Zeichenquelle und numerischen Ziel  
 Es folgen die Regeln zum Konvertieren aus einer Zeichenquelle (CS) zu einem numerischen Ziel (NT):  
  
1.  Ersetzen Sie CS, mit dem Wert, der durch das Entfernen von führenden oder nachfolgenden Leerzeichen in CS abgerufen. Wenn CS kein gültiger ist *numerischen Literalen*, SQLSTATE 22018 (Ungültiger Zeichenwert für Konvertierungsangabe) wird zurückgegeben.  
  
2.  Ersetzen Sie CS, durch den Wert durch das Entfernen der führender Nullen vor dem Dezimaltrennzeichen, nachfolgende Nullen hinter dem Dezimaltrennzeichen oder beides.  
  
3.  Konvertieren Sie CS, NT. Wenn die Konvertierung in einen Verlust signifikanter Ziffern, wird die SQLSTATE 22003 (numerischer Wert außerhalb des gültigen Bereichs) zurückgegeben. Wenn die Konvertierung zum Verlust der nicht signifikante Ziffern SQLSTATE 01 s 07 (Teilbereiche wurden abgeschnitten) wird zurückgegeben.  
  
## <a name="numeric-source-to-character-target"></a>Numerische Zeichen-Ziel die Quelle  
 Es folgen die Regeln zum Konvertieren aus einer numerischen Quelle (NS) zu einem Ziel Zeichen (CT):  
  
1.  Lassen Sie die Länge in Zeichen des CT LT Für die Zuweisung von Abrufen ist die LT gleich der Länge des Puffers in Zeichen minus der Anzahl der Bytes in den Null-Terminierungszeichen für diesen Zeichensatz.  
  
2.  Fälle:  
  
    -   Wenn NS einen exakten numerischen Typ ist, lassen Sie dann auf die kürzeste Zeichenfolge entspricht, das die Definition der entspricht, YP *exakte numerische-literalen* , dass die Skalierung der YP identisch mit der Skala NS, und der interpretierten Wert YP ist die absoluter Wert von NS.  
  
    -   Wenn NS einen ungefähren numerischen Typ ist, dann können Sie YP, die eine Zeichenfolge wie folgt lauten:  
  
         Fall:  
  
         NS ist gleich 0, klicken Sie dann YP 0.  
  
         Können Sie die kürzesten Zeichenfolge sein, die die Definition von exakten - entspricht, YSN*numerischen Literalen* und dessen interpretierten Wert ist der Absolute Wert des NS. Wenn die Länge des YSN ist kleiner als der (*Genauigkeit* + 1) des Datentyps von NS, lassen Sie YP YSN gleich.  
  
         YP ist, andernfalls die kürzesten Zeichenfolge, die die Definition der entspricht *ungefähren numerischen-Literalen* , deren interpretierten Wert ist der Absolute Wert von NS und deren *Mantisse* besteht aus einem einzelne *Ziffer* , nicht "0", gefolgt von einer *Zeitraum* und *unsigned Integer*.  
  
3.  Fall:  
  
    -   Wenn NS kleiner als 0 ist, dann können Sie Y, die das Ergebnis sein:  
  
         '-' &AMP;#124; &AMP;#124; YP  
  
         wobei "&#124;&#124;" der Operator für zeichenfolgenverkettungen ist.  
  
         Andernfalls können Sie YP gleich Y.  
  
4.  Lassen Sie LY, die die Länge in Zeichen von Y.  
  
5.  Fall:  
  
    -   Wenn LY LT gleich ist, ist Klicken Sie dann CT y festgelegt.  
  
    -   Wenn weniger als LT ist, wird CT y auf der rechten Seite Erweiterte um entsprechende Anzahl von Leerzeichen festgelegt.  
  
         Andernfalls (LY > LT), kopieren Sie die ersten Zeichen der LT von Y in CT läuft.  
  
         Fall:  
  
         Ist dies eine Store-Zuweisung, gibt Sie den Fehler SQLSTATE 22001 (Zeichenfolgendaten, rechts abgeschnitten) zurück.  
  
         Ist dies Abruf-Zuweisung, geben Sie die Warnung SQLSTATE 01004 (Zeichenfolgendaten, rechts abgeschnitten) zurück. Wenn die Kopie der Verlust von Dezimalstellen (mit Ausnahme des nachgestellten Nullen) ergibt, ist es treiberdefinierten, ob eine der folgenden Bedingungen zutrifft:  
  
         (1) der Treiber schneidet die Zeichenfolge in Y, die eine geeignete Größe (die 0 (null) kann auch sein), und schreibt das Ergebnis in CT läuft.  
  
         (2) der Treiber wird die Zeichenfolge in Y, die eine geeignete Größe (die 0 (null) kann auch sein), und schreibt das Ergebnis in CT läuft.  
  
         (3) der Treiber, den keine schneidet noch rundet, den aber nur die ersten Zeichen der LT von Y in CT kopiert

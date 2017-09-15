---
title: "Формат файла (драйвера текстового файла) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- delimited text lines
- fixed-width text files
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: f53cd4b5-0721-4562-a90f-4c55e6030cb9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eb3505a7750bf2b538078139cf84b9e88a7e23bd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="text-file-format-text-file-driver"></a>Формат файла (драйвера текстового файла)
Текстовый драйвер ODBC поддерживает оба файла с разделителями и фиксированной ширины текста. Текстовый файл состоит из необязательного заголовка строки и ноль или более строк текста.  
  
 Несмотря на то, что строки заголовка используется тот же формат, как другие строки в текстовом файле, текстовый драйвер ODBC интерпретирует записи строки заголовка, как имена столбцов, а не данные.  
  
 Строка с разделителями содержит одно или несколько значений данных, разделенных разделители: запятые, табуляцию или пользовательский разделитель. Же разделитель, который должен использоваться в файле. Значения NULL, обозначаются с помощью двух разделителей в строке с данными, между ними. Строки символов в строке с разделителями могут быть заключены в двойные кавычки (»»). Без пропусков может возникнуть до или после значений с разделителями.  
  
 Ширина каждой записи данных в строку фиксированной ширины текста указывается в схеме. Значения NULL обозначены пустые значения.  
  
 Таблицы ограничен до 255 полей. Имена полей ограничен 64 символов, и ширину полей ограничены 32 766 символов. Записи не более 65 000 байт.  
  
 Текстовый файл можно открыть только для одного пользователя. Несколько пользователей не поддерживаются.  
  
 Следующие грамматики, написанные для программистов, определяющий формат текстовый файл, который может быть прочитан текстовый драйвер ODBC:  
  
|Формат|Представление|  
|------------|--------------------|  
|Не курсив|Символы, которые должны вводиться, как показано|  
|*курсив*|Аргументы, которые определены в другом месте в грамматике|  
|квадратные скобки ([])|Необязательные элементы|  
|фигурные скобки ({})|Список взаимоисключающих вариантов|  
|вертикальные полосы (&#124;)|Отдельные взаимоисключающих вариантов.|  
|многоточие (...)|Элементы, которые может повторяться один или несколько раз.|  
  
 Текстового файла выглядит следующим образом:  
  
```  
text-file ::=  
   [delimited-header-line] [delimited-text-line]... end-of-file |  
   [fixed-width-header-line] [fixed-width-text-line]... end-of-file  
delimited-header-line ::= delimited-text-line  
delimited-text-line ::=  
   blank-line |  
   delimited-data [delimiter delimited-data]... end-of-line  
fixed-width-header-line ::= fixed-width-text-line  
fixed-width-text-line ::=  
   blank-line |  
   fixed-width-data [fixed-width-data]... end-of-line  
end-of-file ::= <EOF>  
blank-line ::= end-of-line  
delimited-data ::= delimited-string | number | date | delimited-null  
fixed-width-data ::= fixed-width-string | number | date | fixed-width-null  
```  
  
> [!NOTE]  
>  Ширина каждого столбца в файле фиксированной ширины задается в файле Schema.ini.  
  
```  
  
      end-of-line ::= <CR> | <LF> | <CR><LF>  
delimited-string ::= unquoted-string | quoted-stringunquoted-string ::= [character | digit] [character | digit | quote-character]...  
quoted-string ::=  
   quote-character  
   [character | digit | delimiter | end-of-line | embedded-quoted-string]...  
   quote-characterembedded-quoted-string ::=   quote-characterquote-character  
   [character | digit | delimiter | end-of-line]  
   quote-characterquote-characterfixed-width-string ::= [character | digit | delimiter | quote-character] ...  
character ::= any character except:  
   delimiterdigitend-of-fileend-of-linequote-characterdigit ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  
delimiter ::= , | <TAB> |   
custom-delimitercustom-delimiter ::= any character except:  
   end-of-fileend-of-linequote-character  
```  
  
> [!NOTE]  
>  Разделитель в разделители текстовый файл указан в файле Schema.ini.  
  
```  
quote-character ::= "  
number ::= exact-number | approximate-number  
exact-number ::= [+ | -] {unsigned-integer[.unsigned-integer] |  
   unsigned-integer. |  
   .unsigned-integer}  
approximate-number ::= exact-number{e | E}[+ | -]unsigned-integer  
unsigned-integer ::= {digit}...  
date ::=  
   mm date-separator dd date-separator yy |  
   mmm date-separator dd date-separator yy |  
   dd date-separator mmm date-separator yy |  
   yyyy date-separator mm date-separator dd |  
   yyyy date-separator mmm date-separator dd  
mm ::= digit [digit]  
dd ::= digit [digit]  
yy ::= digit digit  
yyyy ::= digit digit digit digit  
mmm ::= Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec  
date-separator ::= - | / | .  
delimited-null ::=  
```  
  
> [!NOTE]  
>  Для файлов с разделителями значение NULL будет представлен нет данных между двумя разделители.  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  Значение NULL для файлов с фиксированной шириной представлен пробелы.

---
title: Формат текстового файла (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- delimited text lines
- fixed-width text files
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: f53cd4b5-0721-4562-a90f-4c55e6030cb9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd2bc95e6fe5468e88fc61dd8ed4adcd985ec052
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62633019"
---
# <a name="text-file-format-text-file-driver"></a>Формат текстового файла (драйвер для текстовых файлов)
Текстовый драйвер ODBC поддерживает оба файла с разделителями и фиксированной ширины текста. Текстовый файл состоит из необязательного заголовка строки и нуль или несколько строк текста.  
  
 Несмотря на то, что строки заголовка используется тот же формат, как другие строки в текстовом файле, текстовый драйвер ODBC интерпретирует записи строки заголовка, как имена столбцов, а не данные.  
  
 Строка с разделителями содержит одно или несколько значений данных, разделенные соответствующими символами: запятые, табуляцию или пользовательский разделитель. Задав должен использоваться в файле. Значения NULL отмечены пометками два разделителя в строке без данных между ними. Строки символов в строку с разделителями могут заключаться в двойные кавычки (»»). Непустые может возникнуть до или после значений с разделителями.  
  
 В схеме задана ширина каждой записи данных в строку фиксированной ширины текста. Значения NULL обозначенное с помощью пустых значений.  
  
 Таблицы, ограничены более 255 полей. Имена полей ограничен 64 символов, и шириной поля ограничены 32 766 символов. Записей ограничено до 65 000 байт.  
  
 Текстовый файл можно открыть только для одного пользователя. Несколько пользователей не поддерживаются.  
  
 Следующей грамматике, написанные для программистов, определяющий формат текстового файла, который можно считать текст драйвером ODBC:  
  
|Формат|Представление|  
|------------|--------------------|  
|Non курсив|Символы, которые должны вводиться, как показано|  
|*Курсив*|Аргументы, которые определяются в грамматике в другом|  
|квадратные скобки ([])|Необязательные элементы|  
|фигурные скобки ({})|Список взаимоисключающих вариантов|  
|вертикальными чертами (&#124;)|Отдельные взаимоисключающих вариантов.|  
|многоточие (...)|Элементы, которые может повторяться один или несколько раз|  
  
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
>  Ширина каждого столбца в файле фиксированной ширины текста задается в файле Schema.ini.  
  
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
>  Файлы с разделителями значение NULL представляются нет данных между двумя разделителями.  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  Значение NULL для файлов с фиксированной шириной, представленного пробелы.

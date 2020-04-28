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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5801433e0180bb07cb2d09a59db2bb74be012cdf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303095"
---
# <a name="text-file-format-text-file-driver"></a>Формат текстового файла (драйвер для текстовых файлов)
Текстовый драйвер ODBC поддерживает текстовые файлы с разделителями и с фиксированной шириной. Текстовый файл состоит из необязательной строки заголовка и нуля или более строк текста.  
  
 Хотя в строке заголовка используется тот же формат, что и в других строках текстового файла, драйвер ODBC Text интерпретирует записи строки заголовка как имена столбцов, а не данные.  
  
 Текстовая строка с разделителями содержит одно или несколько значений данных, разделенных разделителями: запятые, табуляция или пользовательский разделитель. Один и тот же разделитель должен использоваться во всем файле. Значения данных null обозначаются двумя разделителями в строке без данных между ними. Символьные строки в текстовой строке с разделителями можно заключать в двойные кавычки (""). Пробелы не могут находиться до или после значений с разделителями.  
  
 Ширина каждой записи данных в текстовой строке с фиксированной шириной задается в схеме. Значения данных null обозначаются пробелами.  
  
 Таблицы ограничены максимум 255 полями. Имена полей ограничены 64 символами, а ширина полей ограничена 32 766 символами. Записи ограничены 65 000 байтами.  
  
 Текстовый файл может быть открыт только для одного пользователя. Несколько пользователей не поддерживаются.  
  
 Следующая грамматика, написанная для программистов, определяет формат текстового файла, который можно прочитать с помощью текстового драйвера ODBC:  
  
|Формат|Представление|  
|------------|--------------------|  
|Не курсив|Символы, которые должны быть указаны, как показано|  
|*курсив*|Аргументы, определенные в других местах грамматики|  
|квадратные скобки ([])|Необязательные элементы|  
|фигурные скобки ({})|Список взаимоисключающих вариантов|  
|вертикальные полосы (&#124;)|Отдельные взаимоисключающие варианты|  
|многоточия (...)|Элементы, которые могут повторяться один или несколько раз|  
  
 Формат текстового файла:  
  
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
>  Ширина каждого столбца в текстовом файле с фиксированной шириной указана в файле Schema. ini.  
  
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
>  Разделитель в текстовом файле с разделителями-задается в файле Schema. ini.  
  
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
>  Для файлов с разделителями значение NULL представляется отсутствием данных между двумя разделителями.  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  Для файлов с фиксированной шириной значение NULL представлено пробелами.

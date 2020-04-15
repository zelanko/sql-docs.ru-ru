---
title: Формат текстовых файлов (Драйвер текстовых файлов) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303095"
---
# <a name="text-file-format-text-file-driver"></a>Формат текстового файла (драйвер для текстовых файлов)
Драйвер текста ODBC поддерживает как делимитированные, так и файлы текста с фиксированной шириной. Текстовый файл состоит из дополнительной строки заголовка и нулевых или более текстовых строк.  
  
 Хотя строка заголовка использует тот же формат, что и другие строки в текстовом файле, драйвер ТЕКСТА ODBC интерпретирует записи заголовка как имена столбцов, а не данные.  
  
 Делимитированный текстовая строка содержит одно или несколько значений данных, разделенных делимитерами: запятые, вкладки или пользовательский делимитер. Один и тот же делимитер должен использоваться во всем файле. Значения данных null обозначаются двумя делимитерами подряд без данных между ними. Строки символов в делимитированной текстовой строке могут быть заключены в двойные кавычки (""). Заготовки не могут возникать до или после разграничения значений.  
  
 Ширина каждой ввода данных в текстовой линии с фиксированной шириной указана в схеме. Значения данных null обозначаются пробелами.  
  
 Таблицы ограничены максимум 255 полями. Названия полей ограничены 64 символами, а ширина полей ограничена 32 766 символами. Записи ограничены 65 000 байтов.  
  
 Текстовый файл может быть открыт только для одного пользователя. Несколько пользователей не поддерживаются.  
  
 Следующая грамматика, написанная для программистов, определяет формат текстового файла, который может быть прочитан драйвером текста ODBC:  
  
|Формат|Представление|  
|------------|--------------------|  
|Не-италики|Символы, которые должны быть введены в виде показаний|  
|*Курсив*|Аргументы, которые определены в других местах в грамматике|  
|скобки (яп. )|Необязательные элементы|  
|скобки{}( )|Список взаимоисключающих вариантов|  
|вертикальные бары (&#124;)|Отдельные взаимоисключающие решения|  
|многоточия (...)|Элементы, которые можно повторить один или несколько раз|  
  
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
>  Ширина каждого столбца в текстовом файле с фиксированной шириной указана в файле Schema.ini.  
  
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
>  Делимитер в файле специально делимитированных текстов указан в файле Schema.ini.  
  
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
>  Для делимитированных файлов NULL не представлен данными между двумя делимитерами.  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  Для файлов с фиксированной шириной NULL представлен пробелами.

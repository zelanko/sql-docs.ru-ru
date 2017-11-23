---
title: "СОЗДАЙТЕ ФОРМАТ ВНЕШНЕГО файла (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL FILE FORMAT
- CREATE_EXTERNAL_FILE_FORMAT
dev_langs: TSQL
helpviewer_keywords:
- External
- External, file format
- PolyBase, external file format
ms.assetid: abd5ec8c-1a0e-4d38-a374-8ce3401bc60c
caps.latest.revision: "25"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 037f9e0da637b872298d3859499858620570bc41
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="create-external-file-format-transact-sql"></a>СОЗДАЙТЕ ФОРМАТ ВНЕШНЕГО файла (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Создает определение формата внешнего файла PolyBase для внешних данных, хранящимся в Hadoop, хранилище больших двоичных объектов или хранилища Озера данных Azure. Создание формата внешних файлов является необходимым условием для создания внешней таблицы PolyBase. При создании формата внешнего файла, укажите фактическая структура данных, ссылается ли таблица внешней.  
  
 PolyBase поддерживает следующие форматы файлов:  
  
-   Текст с разделителями  
  
-   Куст RCFile  
  
-   Куст ORC.  
  
-   Parquet  
  
 Чтобы создать внешнюю таблицу, в разделе [CREATE EXTERNAL TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-table-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Create an external file format for PARQUET files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = PARQUET  
     [ , DATA_COMPRESSION = {  
        'org.apache.hadoop.io.compress.SnappyCodec'  
      | 'org.apache.hadoop.io.compress.GzipCodec'      }  
    ]);  
  
--Create an external file format for ORC files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = ORC  
     [ , DATA_COMPRESSION = {  
        'org.apache.hadoop.io.compress.SnappyCodec'  
      | 'org.apache.hadoop.io.compress.DefaultCodec'      }  
    ]);  
  
--Create an external file format for RCFILE.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = {  
        'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
      | 'org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe'  
    }  
    [ , DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec' ]);  
  
--Create an external file format for DELIMITED TEXT files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT  
    [ , FORMAT_OPTIONS ( <format_options> [ ,...n  ] ) ]  
    [ , DATA_COMPRESSION = {  
           'org.apache.hadoop.io.compress.GzipCodec'  
         | 'org.apache.hadoop.io.compress.DefaultCodec'  
        }  
     ]);  
  
<format_options> ::=  
{  
    FIELD_TERMINATOR = field_terminator  
    | STRING_DELIMITER = string_delimiter  
    | DATE_FORMAT = datetime_format  
    | USE_TYPE_DEFAULT = { TRUE | FALSE } 
    | Encoding = {'UTF8' | 'UTF16'} 
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *file_format_name*  
 Указывает имя формата внешнего файла.  
  
 FORMAT_TYPE  
 Задает формат внешних данных.  
  
 PARQUET  
 Задает формат Parquet.  
  
 ORC.  
 Указывает формат оптимизирован строк по столбцам (ORC.). Этот параметр требует версию 0.11 или более поздней версии на внешних кластера Hadoop Hive. В Hadoop формат файлов ORC обеспечивает повышения сжатия и производительность по сравнению с RCFILE формат файла.  
  
 RCFILE (в сочетании с SERDE_METHOD = *SERDE_method*)  
 Задает один столбец записи формат файла (RcFile). Этот параметр, необходимо указать сериализатор Hive и метод десериализатор (SerDe). Это требование одинаково при использовании Hive или HiveQL в Hadoop для запроса RC-файлы. Обратите внимание, что "метод serde" учитывается регистр символов.  
  
 Примеры указания RCFile с двумя SerDe методами, которые поддерживает PolyBase.  
  
-   FORMAT_TYPE = RCFILE SERDE_METHOD = «org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe»  
  
-   FORMAT_TYPE = RCFILE SERDE_METHOD = «org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe»  
  
 DELIMITEDTEXT  
 Указывает в текстовом формате с разделителями столбец, также называемый признаки конца поля.  
  
 Признак_конца_поля = *признак_конца_поля*  
 Применяется только для текстовых файлов с разделителями. Указывает один или несколько символов, отмечающий конец каждого поля (столбца) в файле с разделителями текста. Значение по умолчанию — ꞌ символ вертикальной черты | ꞌ. Для гарантированного поддержки рекомендуется использовать один или несколько символов ascii.
  
  
 Примеры:  
  
-   ПРИЗНАК_КОНЦА_ПОЛЯ = "|"  
  
-   ПРИЗНАК_КОНЦА_ПОЛЯ = ""  
  
-   Признак_конца_поля = ꞌ\tꞌ  
  
-   ПРИЗНАК_КОНЦА_ПОЛЯ = "~ | ~"  
  
 STRING_DELIMITER = *string_delimiter*  
 Указывает признак конца поля данных строкового типа в файле с разделителями текста. Разделитель строк длиной в один или несколько символов и заключено в одинарные кавычки. Значение по умолчанию — пустая строка «». Для гарантированного поддержки рекомендуется использовать один или несколько символов ascii.
 
  
 Примеры:  

-   STRING_DELIMITER = "»"

-   STRING_DELIMITER = "0x22»--hex двойная кавычка
  
-   STRING_DELIMITER = "*"  
  
-   STRING_DELIMITER = Ꞌ Ꞌ  
  
-   STRING_DELIMITER = «0x7E0x7E»--два tildas (например ~ ~)
  
 DATE_FORMAT = *datetime_format*  
 Задает пользовательский формат для всех данных даты и времени, которые могут отображаться в текстовом файле с разделителями. Если исходный файл использует форматы datefime по умолчанию, этот параметр необязателен. Файл разрешен только один пользовательского формата datetime. Нельзя указать несколько форматов пользовательских даты и времени каждого файла. Тем не менее можно использовать несколько форматов даты и времени, если каждый из них является форматом по умолчанию для его типа данных в определении внешней таблицы.
 
 
PolyBase использует только пользовательский формат для импорта данных. Он не использует пользовательский формат для записи данных во внешний файл.

 Если DATE_FORMAT не указан или является пустой строкой, PolyBase будет использовать следующие форматы по умолчанию:  
  
-   DateTime: «гггг мм дд чч'  
  
-   SmallDateTime: «гггг мм дд чч: мм»  
  
-   Дата: «гггг мм дд»  
  
-   DateTime2: «гггг мм дд чч'  
  
-   DateTimeOffset: «гггг мм дд чч'  
  
-   Время: «ЧЧ'  
  
 **Форматы даты пример** находятся в следующей таблице.  
  
 Примечания о таблице.  
  
-   Год, месяц и день могут иметь различные форматы и заказов. В таблице представлены только «гмд». Месяц может иметь цифры 1 или 2 или 3 символов. День могут иметь 1 или 2 цифрами. Год может содержать два или четыре цифры.  
  
-   Миллисекунды (fffffff) не является обязательным.  
  
-   AM, pm (tt) не является обязательным. Значение по умолчанию — AM.  
  
|Date-тип|Пример|Description|  
|---------------|-------------|-----------------|  
|DateTime|DATE_FORMAT = «гггг мм дд чч:мм:сс.мс»|Помимо год, месяц и день, в нем 00 – 24 часа 00-59 минут 00-59 секунд и миллисекунд 3 цифр.|  
|DateTime|DATE_FORMAT = «гггг мм дд hh:mm:ss.ffftt»|Помимо год, месяц и день, в нем 00 12 часов 00-59 минут 00-59 секунд, 3 цифр для миллисекунд и AM, am, PM или pm.|  
|SmallDateTime|DATE_FORMAT = «гггг мм дд чч: мм»|Помимо год, месяц и день, в нем 00-23 часа 00-59 минут.|  
|SmallDateTime|DATE_FORMAT = «гггг мм дд hh:mmtt»|Помимо год, месяц и день, в нем 00 11 часов, минут 00-59, без секунд и AM, am, PM или pm.|  
|Дата|DATE_FORMAT = «гггг мм дд»|Год, месяц и день. Элемент времени не включено.|  
|Дата|DATE_FORMAT = «гггг мм дд»|Год, месяц и день. Если месяц указывается с 3 МБ, входное значение является одной или строк, янв, фев, мар, апр, май, июн, июл, авг, сен октября, ноября и декабря.|  
|datetime2|DATE_FORMAT = «yyyy-MM-dd HH:mm:ss.fffffff»|Помимо год, месяц и день, в нем 00-23 часа 00-59 минут 00-59 секунд до 7 цифр, для миллисекунд.|  
|datetime2|DATE_FORMAT = «гггг мм дд hh:mm:ss.ffffffftt»|Помимо год, месяц и день, в нем 00 11 часов 00-59 минут 00-59 сек., 7 цифр для миллисекунд и AM, am, PM или pm.|  
|DateTimeOffset|DATE_FORMAT = «yyyy-MM-dd HH:mm:ss.fffffff zzz»|Помимо год, месяц и день, в нем 00-23 часа 00-59 минут 00-59 секунд до 7 цифр, для миллисекунд и смещения часового пояса, которая помещается во входном файле как {+ &#124;-} HH:ss. Например, со времени Лос-Анджелес, без перехода на летнее экономия — 8 часов раньше времени UTC, значение -08:00 во входном файле указывает часовой пояс для Лос-Анджелес.|  
|DateTimeOffset|DATE_FORMAT = «гггг мм дд hh:mm:ss.ffffffftt zzz»|Помимо год, месяц и день, в нем 00 11 часов 00-59 минут 00-59 секунд, 7 цифр для миллисекунд (AM, am, PM или pm) и смещение часового пояса. См. в описании в предыдущей строке.|  
|Time|DATE_FORMAT = 'Чч'|Нет значения даты, только 00-23 часа 00-59 минут и 00-59 секунд.|  
  
 Все поддерживаемые форматы даты:  
  
|datetime|smalldatetime|date|datetime2|datetimeoffset|  
|--------------|-------------------|----------|---------------|--------------------|  
|[M [M]] -M [d]-d [гг] ГГ ЧЧ [.fff]|[M [M]] -M [d]-d [гг] ГГ ЧЧ: мм [: 00]|[M [M]] -M [d]-d [гг] гг|[M [M]] -M [d]-d [гг] ГГ ЧЧ [.fffffff]|[M [M]] M — [d]-d [гг] ГГ ЧЧ [.fffffff] zzz|  
|[M [M]] M — [d]-d [гг] ГГ ЧЧ [.fff] [Тт]|[M [M]] M — [d]-d [гг] ГГ ЧЧ: мм [: 00] [Тт]||[M [M]] M — [d]-d [гг] ГГ ЧЧ [.fffffff] [Тт]|[M [M]] M — [d]-d [гг] ГГ ЧЧ [.fffffff] [Тт] zzz|  
|[M [M]] -M [гг] гг-[d] d чч [.fff]|[M [M]] -M [гг] гг-[d] d hh: mm [: 00]|[M [M]] -M [гг] гг-[d] d|[M [M]] -M [гг] гг-[d] d чч [.fffffff]|[M [M]] -M [гг] гг-[d] d zzz чч [.fffffff]|  
|[M [M]] M — [гг] гг-[d] чч d [.fff] [Тт]|[M [M]] M — [гг] гг-[d] d hh: mm [: 00] [Тт]||[M [M]] M — [гг] гг-[d] чч d [.fffffff] [Тт]|[M [M]] M — [гг] гг-[d] чч d [.fffffff] [Тт] zzz|  
|[гг] гг-[M [M]]-M [d] d чч [.fff]|[гг] гг-[M [M]]-M [d] d hh: mm [: 00]|[гг] гг-[M [M]]-M [d] d|[гг] гг-[M [M]]-M [d] d чч [.fffffff]|[гг] гг-[M [M]]-M [d] чч d [.fffffff] zzz|  
|[гг] гг-[M [M]]-M [d] d чч [.fff] [Тт]|[гг] гг-[M [M]]-M [d] d hh: mm [: 00] [Тт]||[гг] гг-[M [M]]-M [d] d чч [.fffffff] [Тт]|[гг] гг-[M [M]]-M [d] d чч [.fffffff] [Тт] zzz|  
|[гг] гг-[d]-d [M [M]] M чч [.fff]|[гг] гг-[d]-d [M [M]] M hh: mm [: 00]|[гг] гг - d [d] - M [M [M]]|[гг] гг-[d]-d [M [M]] M чч [.fffffff]|[гг] гг-[d]-d [M [M]] чч M [.fffffff] zzz|  
|[гг] гг-[d]-d [M [M]] M чч [.fff] [Тт]|[гг] гг-[d]-d [M [M]] M hh: mm [: 00] [Тт]||[гг] гг-[d]-d [M [M]] M чч [.fffffff] [Тт]|[гг] гг-[d]-d [M [M]] M чч [.fffffff] [Тт] zzz|  
|[d]-d [M [M]]-M [гг] ГГ ЧЧ [.fff]|[d]-d [M [M]]-M [гг] ГГ ЧЧ: мм [: 00]|[d]-d [M [M]]-M [гг] гг|[d]-d [M [M]]-M [гг] ГГ ЧЧ [.fffffff]|[d]-d [M [M]]-M [гг] ГГ ЧЧ [.fffffff] zzz|  
|[d]-d [M [M]]-M [гг] ГГ ЧЧ [.fff] [Тт]|[d]-d [M [M]]-M [гг] ГГ ЧЧ: мм [: 00] [Тт]||[d]-d [M [M]]-M [гг] ГГ ЧЧ [.fffffff] [Тт]|[d]-d [M [M]]-M [гг] ГГ ЧЧ [.fffffff] [Тт] zzz|  
|[d] d-[гг] гг-[M [M]] M чч [.fff]|[d] d-[гг] гг-[M [M]] M hh: mm [: 00]|[d] d-[гг] гг-[M [M]] M|[d] d-[гг] гг-[M [M]] M чч [.fffffff]|[d]-d [гг] гг-[M [M]] чч M [.fffffff] zzz|  
|[d]-d [гг] гг-[M [M]] M чч [.fff] [Тт]|[d]-d [гг] гг-[M [M]] M hh: mm [: 00] [Тт]||[d]-d [гг] гг-[M [M]] M чч [.fffffff] [Тт]|[d]-d [гг] гг-[M [M]] M чч [.fffffff] [Тт] zzz|  
  
 Подробные сведения:  
  
-   Разделяйте месяц, день и год, можно использовать '—', '/' или '. '. Для простоты в таблице используется только в качестве разделителя «—».  
  
-   Чтобы указать месяца в виде текста используйте три или более символов. Месяцы 1 или 2 знаков будет интерпретироваться как число.  
  
-   Для разделения значений времени, используйте ":" символ.  
  
-   Буквы, заключенных в квадратные скобки, являются необязательными.  
  
-   Назначение буквы «tt» [AM | PM | am | pm]. ПО умолчанию. Если выбрано «tt», значение часа (ЧЧ) должен быть в диапазоне от 0 до 12.  
  
-   Буквы «zzz» указать смещение часового пояса для текущего часового пояса в системе в формате {+ |-} HH:ss].  
  
 USE_TYPE_DEFAULT = {TRUE | **FALSE** }  
 Указывает способ обработки отсутствующих значений в текстовых файлов с разделителями, когда PolyBase получает данные из текстового файла.  
  
 TRUE  
 При получении данных из текстового файла, сохраните каждое значение отсутствует, используется значение по умолчанию для типа данных соответствующего столбца в определении внешней таблицы. Например Замените отсутствующие значения с:  
  
-   0, если столбец определен как числового столбца.  
  
-   Пустая строка «» Если столбец имеет строковый столбец.  
  
-   1900-01-01, если столбец является столбцом дат.  
  
 FALSE  
 Сохранить все отсутствующие значения как NULL. ПУСТЫЕ значения, сохраненные с помощью слово NULL в файле с разделителями, импортируется как строку «NULL».  
  
   Кодирование = {'UTF8' | «UTF16»}   
 В хранилище данных SQL Azure PolyBase можно прочитать UTF8 и UTF16-LE кодировке с разделителями текстовых файлов. В SQL Server и PDW, PolyBase не поддерживает чтение UTF16 файлы в кодировке.
  
 DATA_COMPRESSION = *data_compression_method*  
 Задает метод сжатия данных для внешних данных. Если DATA_COMPRESSION не указан, значение по умолчанию — несжатых данных.  
 Для правильной работы Gzip сжатые файлы должны иметь расширение файла «.gz».
 
 Тип формата DELIMITEDTEXT поддерживает следующие методы сжатия:  
  
-   СЖАТИЕ данных = «org.apache.hadoop.io.compress.DefaultCodec»  
  
-   СЖАТИЕ данных = «org.apache.hadoop.io.compress.GzipCodec»  

 Для типа формата RCFILE поддерживает этот метод сжатия:  
  
-   СЖАТИЕ данных = «org.apache.hadoop.io.compress.DefaultCodec»  
  
 Тип формат файлов ORC поддерживает следующие методы сжатия:  
  
-   СЖАТИЕ данных = «org.apache.hadoop.io.compress.DefaultCodec»  
  
-   СЖАТИЕ данных = «org.apache.hadoop.io.compress.SnappyCodec»  
  
 Тип формата файлов PARQUET поддерживает следующие методы сжатия:  
  
-   СЖАТИЕ данных = «org.apache.hadoop.io.compress.GzipCodec»  
  
-   СЖАТИЕ данных = «org.apache.hadoop.io.compress.SnappyCodec»  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY EXTERNAL FILE FORMAT.  
  
## <a name="general-remarks"></a>Общие замечания  
 Формат внешнего файла уровня базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Это уровня сервера в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 Параметры формата являются необязательными и применяются только для текстовых файлов с разделителями.  
  
 Если данные хранятся в одном из форматов сжатые, PolyBase сначала распаковки данных перед возвратом записей данных.  
  
## <a name="limitations-and-restrictions"></a>Ограничения   
  
 Разделитель строк в файлы с разделителями запятыми, которые должны поддерживаться, LineRecordReader Hadoop т.е. он должен быть «\r», «\n» или «\r\n». Они не настраивается пользователем.  
  
 Сочетание поддерживаемых методов SerDe с RCFiles и методы сжатия данных, поддерживаемые перечисленных ранее в этой статье. Поддерживаются не все сочетания.  
  
 Максимальное число одновременных запросов PolyBase — 32. При выполнении 32 параллельных запросов, каждый запрос может прочитать более 33,000 файлов из расположения внешнего файла. Корневая папка и Каждая вложенная папка также учитывается как файл. Если степень параллелизма меньше 32, расположение внешнего файла может содержать более 33,000 файлов.  
  
 Из-за ограничения на количество файлов во внешней таблице рекомендуется хранить не более 30 000 файлы в корневой и вложенные папки из расположения внешнего файла. Кроме того рекомендуется оставлять число вложенные папки в корневом каталоге небольшому числу. При обращении к слишком много файлов, может возникнуть исключение нехватки памяти в виртуальной машине Java.  
  
## <a name="locking"></a>Блокировка  
 Принимает разделяемую блокировку объекта ФОРМАТА ВНЕШНЕГО файла.  
  
## <a name="performance"></a>Производительность  
 С помощью сжатых файлов всегда поставляется с компромисса между передачи меньше данных между внешним источником данных и SQL Server, увеличивая ЦП для сжатия и распаковки данных.  
  
 Текстовые файлы сжимаются gzip не разбить таблицу. Чтобы повысить производительность для сжатых Gzip текстовых файлов, рекомендуется создание нескольких файлов, которые хранятся в том же каталоге, в пределах внешнего источника данных. Это позволяет PolyBase для чтения и распаковки данных быстрее с помощью нескольких процессов чтения и распаковки. Оптимальное количество сжатых файлов — максимальное число процессов чтения данных на вычислительном узле. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], максимальное число процессов чтения данных составляет 8 на каждом узле в текущем выпуске. В [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], максимальное число процессов чтения данных каждого узла зависит от цели уровня Обслуживания. В разделе [хранилище данных SQL Azure, загрузка шаблонов и стратегии](https://blogs.msdn.microsoft.com/sqlcat/2016/02/06/azure-sql-data-warehouse-loading-patterns-and-strategies/) подробные сведения.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-create-a-delimitedtext-external-file-format"></a>A. Создайте формат внешнего файла DELIMITEDTEXT  
 В этом примере создается с именем формата внешних файлов *textdelimited1* для файла с разделителями текста. Укажите FORMAT_OPTIONS полей в файле разделяются символом вертикальной черты "|". Текстовый файл также сжаты с использованием кодека Gzip. Если DATA_COMPRESSION не указан, текстовом файле без сжатия.  
  
 Для файла с разделителями, метод сжатия данных может быть значение по умолчанию кодек, «org.apache.hadoop.io.compress.DefaultCodec» или кодек Gzip «org.apache.hadoop.io.compress.GzipCodec».  
  
```  
CREATE EXTERNAL FILE FORMAT textdelimited1  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT,  
    FORMAT_OPTIONS (  
        FIELD_TERMINATOR = '|',  
        DATE_FORMAT = 'MM/dd/yyyy' ),  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.GzipCodec'  
);  
```  
  
### <a name="b-create-an-rcfile-external-file-format"></a>Б. Создайте формат внешнего файла RCFile  
 Этот пример создает формата внешних файлов для RCFile, использующий org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe метод сериализации или десериализации. Он также указывает кодек по умолчанию для метода сжатия данных. Если DATA_COMPRESSION не указан, значение по умолчанию — без сжатия.  
  
```  
CREATE EXTERNAL FILE FORMAT rcfile1  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe',  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec'  
);  
```  
  
### <a name="c-create-an-orc-external-file-format"></a>В. Создайте формат внешнего файла ORC.  
 Этот пример создает формата внешнего файла для файла, сжатие данных с помощью метода сжатия данных org.apache.io.compress.SnappyCodec ORC. Если DATA_COMPRESSION не указан, значение по умолчанию — без сжатия.  
  
```  
CREATE EXTERNAL FILE FORMAT orcfile1  
WITH (  
    FORMAT_TYPE = ORC,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
### <a name="d-create-a-parquet-external-file-format"></a>Г. Создайте формат внешнего файла PARQUET  
 В этом примере создается файл Parquet, сжатие данных с помощью метода сжатия данных org.apache.io.compress.SnappyCodec формата внешних файлов. Если DATA_COMPRESSION не указан, значение по умолчанию — без сжатия.  
  
```  
CREATE EXTERNAL FILE FORMAT parquetfile1  
WITH (  
    FORMAT_TYPE = PARQUET,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)   
 [СОЗДАТЬ внешний TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT #40; Хранилище данных Azure SQL &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [sys.external_file_formats (Transact-SQL)](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)  
  
  

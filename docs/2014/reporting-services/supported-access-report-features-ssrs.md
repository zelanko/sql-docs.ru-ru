---
title: Поддерживаемые функции отчетов Access (SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], Access reports
- functions [Reporting Services]
- controls [Reporting Services]
- Access reports [Reporting Services]
- properties [Reporting Services], Access reports
- importing reports
- modules [Reporting Services]
ms.assetid: 7ffec331-6365-4c13-8e58-b77a48cffb44
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9088ab3e90b4fb341cc8125e45d498783953039d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100579"
---
# <a name="supported-access-report-features-ssrs"></a>Поддерживаемые функции отчетов Access (службы SSRS)
  Когда отчет импортируется в конструктор отчетов, процесс импорта преобразует отчет [!INCLUDE[msCoName](../includes/msconame-md.md)] Access в RDL-файл служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. 'Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживает некоторое число функций Access, но из-за различий между Access и [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] часть элементов может быть слегка изменена или не поддерживаться. В этом разделе описано преобразование функций отчетов Access в функции на языке определения отчетов.  
  
## <a name="importing-access-reports"></a>Импорт отчетов Access  
 Некоторые запросы содержат специальный код Access. Этот код не импортируется вместе с отчетом. Кроме того, если запрос содержит внедренные строки, то отчет может импортироваться неправильно. В этом случае необходимо заменить строки кодами символов. Например, запятую (,) нужно заменить на «CHAR(34)».  
  
 В процессе импорта точка с запятой не передается должным образом (;) или символы разметки XML\<(, > и т. д.) в сведениях строки подключения. Если строка соединения содержит такой символ, то необходимо вручную задать пароль в новом отчете после импорта.  
  
 Параметры соединения и общего времени ожидания в строке соединения не импортируются. Эти параметры можно настроить после импорта отчета.  
  
 При импорте отчета не преобразуются запросы, содержащие параметры. Чтобы импортировать запрос вместе с отчетом, временно замените параметры запроса в отчете Access фиксированными значениями и заново замените их нужными параметрами после импорта отчета.  
  
## <a name="page-layout"></a>Макет страницы  
 Отчеты Access и служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] имеют разные макеты страниц. Access упорядочивает элементы на странице, используя «полосы», то есть разделы на странице располагаются вертикально. Эти разделы могут включать заголовок отчета, нижний колонтитул отчета, верхний и нижний колонтитулы страницы, группы и подробные сведения. 'Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обеспечивает более гибкий формат. Области данных предоставляют возможности группирования и отображения подробных сведений; многочисленные области данных можно размещать в любых местах текста отчета, в том числе и рядом друг с другом. 'Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] включают также «ленточный» верхний и нижний колонтитулы страницы, подобные верхнему и нижнему колонтитулам страницы в Access.  
  
 Если отчет импортируется из Access в конструктор отчетов, верхний и нижний колонтитулы страницы Access преобразуются в верхний и нижний колонтитулы отчета служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Группы и подробности преобразуются в списочную область данных. Верхний и нижний колонтитулы помещаются в текст отчета, а не в отдельные полосы. Это приводит к тому, что расположение элементов немного отличается от макета отчета Access.  
  
> [!NOTE]  
>  В некоторых отчетах Access элементы отчета, которые на первый взгляд располагаются рядом, могут в действительности перекрываться. Если импорт отчета выполнялся с помощью конструктора отчетов, это перекрытие не корректируется и может привести к непредвиденным результатам при запуске отчета.  
  
## <a name="data-sources"></a>обозревателе решений  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают источники данных OLE DB, такие как [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При импорте отчета из файла проекта Access (ADP) строка подключения для источника данных извлекается из этого файла. При импорте отчета из файла базы данных Access (MDB или ACCDB) строка соединения может указывать на базу данных Access. В этом случае ее придется изменить после импорта. Если источником данных отчета Access является запрос, то данные запроса импортируются в RDL-файл без изменений. Если источником данных отчета Access является таблица, то в процессе преобразования запрос создается на основе имени и полей таблицы.  
  
## <a name="reports-with-custom-modules"></a>Отчеты с пользовательскими модулями  
 Если в модулях [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] содержится пользовательский код, он не преобразуется. Если конструктор отчетов встречает код во время импорта, создается предупреждение, которое отображается в окне **список задач** .  
  
## <a name="report-controls"></a>Элементы управления отчетом  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие элементы управления Access, которые помещаются в преобразованные определения отчетов.  
  
|||||  
|-|-|-|-|  
|Изображение|Метка|график;|Прямоугольник|  
|SubForm|SubReport<br /><br /> **Примечание** . При преобразовании элемента управления вложенного отчета в основной отчет сам вложенный отчет преобразуется отдельно.|TextBox||  
  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие элементы управления:  
  
|||||  
|-|-|-|-|  
|BoundObjectFrame|CheckBox|ComboBox|CommandButton|  
|CustomControl|ListBox|ObjectFrame|OptionButton|  
|TabControl|ToggleButton|||  
  
 Если конструктор отчетов обнаруживает какой-либо из этих элементов управления во время импорта, создается предупреждение, которое отображается в окне **список задач** .  
  
 Такие элементы управления, как ActiveX и веб-компоненты Office, не импортируются. Например, если отчет Access содержит элемент управления «Диаграмма веб-компонентов Office», то этот элемент не будет преобразован при импорте.  
  
## <a name="report-properties"></a>Свойства отчета  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие свойства, доступные в пользовательском интерфейсе Access. Свойства, доступные только в коде, не поддерживаются и не перечисляются ниже.  
  
|||||  
|-|-|-|-|  
|BackColor|BackStyle|BorderColor|BorderStyle|  
|BorderWidth|BottomMargin|CanGrow (текстовое поле)|CanShrink (текстовое поле)|  
|Caption|FontBold|FontItalic|FontName|  
|FontSize|FontUnderline|FontWeight|ForceNewPage|  
|ForeColor|Высота:|HideDuplicates|Hyperlink|  
|IsHyperlink|IsVisible|KeepTogether (группа)|Слева|  
|LeftMargin|LineSlant|LineSpacing|LinkChildFields|  
|LinkMasterFields|NewRowOrCol|PageFooter|PageHeader|  
|Страницы|Рисунок|PictureTiling (отчет)|ReadingOrder|  
|RepeatSection|RightMargin|RunningSum|SizeMode|  
|TextAlign|TOP|TopMargin|Ширина|  
  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие свойства, доступные в пользовательском интерфейсе Access.  
  
|||||  
|-|-|-|-|  
|CanGrow (раздел)|CanShrink (раздел)|DecimalPlaces|FastLaserPrinting|  
|Filter|FilterOn|Формат|FormatConditions|  
|GrpKeepTogether|KeepTogether (раздел)|NumeralShapes|Ориентация|  
|PaintPalette|PaletteSource|PictureAlignment|PicturePages|  
|PictureSizeMode|PictureTiling (изображение)|ScrollBars|SpecialEffect|  
|Vertical||||  
  
## <a name="grouping"></a>Группирование  
 В Access уровень групп определяется сочетанием трех свойств: выражением группы, свойством `GroupOn` и свойством `GroupInterval`. Группа, у которой отсутствуют верхний и нижний колонтитулы, объединяется с группой, которую она содержит. Если группа не содержит других групп, то сортировка применяется ко всему разделу и группа удаляется.  
  
## <a name="expressions"></a>Выражения  
 С помощью выражений в Access задаются значения, отображаемые в текстовых полях. В качестве языка выражений в Access используется [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] и некоторые агрегатные функции. Конструктор отчетов преобразует эти выражения Access в выражения отчета.  
  
### <a name="functions"></a>Функции  
 В качестве собственного языка выражений определения отчета службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] используют [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET, а Access 2002 — Visual Basic. В следующей таблице содержится список функций, поддерживаемых службами [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
#### <a name="array-functions"></a>Функции массивов  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие функции массивов:  
  
-   LBound  
  
-   UBound  
  
#### <a name="conversion-functions"></a>Функции преобразования  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие функции преобразования.  
  
|||||  
|-|-|-|-|  
|Asc|CBool|CByte|CCur|  
|CDate|CDbl|CDec|Chr|  
|Chr$|CInt|CLng|CSng|  
|CStr|CVar|CVDate|Формат|  
|FormatCurrency|FormatDateTime|FormatNumber|FormatPercent|  
|Hex|Hex$|Nz|Окт|  
|Oct$|Str|Str$|StrConv|  
|Val||||  
  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие функции преобразования:  
  
-   GUIDFromString  
  
-   StringFromGUID  
  
#### <a name="database-functions"></a>Функции базы данных  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие функции базы данных.  
  
|||||  
|-|-|-|-|  
|CreateReport|GetObject|HyperlinkPart|Секция|  
  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие функции базы данных.  
  
|||||  
|-|-|-|-|  
|CodeDb|CreateControl|CreateForm|CreateGroupLevel|  
|CreateObject|CreateReportControl|CurrentDb|CurrentUser|  
|DeleteControl|DeleteReportControl|Eval|IMEStatus|  
|SysCmd||||  
  
#### <a name="datetime-functions"></a>Функции даты/времени  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие функции даты-времени.  
  
|||||  
|-|-|-|-|  
|Дата|Date$|DateAdd|DateDiff|  
|DatePart|DateSerial|DateValue|День|  
|Час|Минута|Месяц|MonthName|  
|Сейчас|Секунда|Время|Time$|  
|Таймер|TimeSerial|TimeValue|День недели|  
|WeekdayName|Год|||  
  
#### <a name="ddeole-functions"></a>Функции DDE/OLE  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие функции DDE/OLE.  
  
|||||  
|-|-|-|-|  
|DDE|DDEIntitate|DDERequest|DDESend|  
|LoadPicture||||  
  
#### <a name="domain-aggregate-functions"></a>Агрегатные функции домена  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие агрегатные функции домена.  
  
|||||  
|-|-|-|-|  
|DAvg|DCount|DFirst|DLast|  
|DLookup|DMax|DMin|DStDev|  
|DStDevP|DSum|DVar|DVarP|  
  
#### <a name="error-handling-functions"></a>Функции обработки ошибок  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие функции обработки ошибок.  
  
|||||  
|-|-|-|-|  
|Err|Ошибка|Error$|IsError|  
  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие функции обработки ошибок.  
  
-   CVErr  
  
#### <a name="financial-functions"></a>Финансовые функции  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие финансовые функции.  
  
|||||  
|-|-|-|-|  
|DDB|FV|IPmt|IRR|  
|MIRR|NPer|NPV|Pmt|  
|PPmt|PV|Тариф|SLN|  
|SYD||||  
  
#### <a name="interaction-functions"></a>Функции взаимодействия  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие функции взаимодействия.  
  
|||||  
|-|-|-|-|  
|Команда|Command$|CurDir|CurDir$|  
|DeleteSetting|Dir|Dir$|Environ|  
|Environ$|EOF|FileAttr|FileDateTime|  
|FileLen|FreeFile|GetAllSettings|GetAttr|  
|GetSetting|Loc|LOF|QBColor|  
|RGB|SaveSetting|Seek|SetAttr|  
|Shell|Spc|Вкладка||  
  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие функции взаимодействия.  
  
|||||  
|-|-|-|-|  
|DoEvents|В|Входные данные|Input$|  
  
#### <a name="inspection-functions"></a>Функции проверки  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие функции проверки.  
  
|||||  
|-|-|-|-|  
|IsArray|IsDate|IsEmpty|IsError|  
|IsNull|IsNumeric|IsObject|TypeName|  
|VarType||||  
  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие функции проверки.  
  
-   IsMissing  
  
#### <a name="math-functions"></a>Математические функции  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие математические функции.  
  
|||||  
|-|-|-|-|  
|Abs|Atn|Cos|Exp|  
|Fix|Int|Журнал|Rnd|  
|Round|Sgn|Sin|Sqr|  
|Tan||||  
  
#### <a name="message-functions"></a>Функции сообщений  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживают следующие функции сообщений.  
  
|||||  
|-|-|-|-|  
|InputBox|InputBox$|MsgBox||  
  
#### <a name="program-flow-functions"></a>Функции управления потоком выполнения программы  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие функции управления программным потоком.  
  
|||||  
|-|-|-|-|  
|Choose|IIf|Параметр||  
  
#### <a name="sql-aggregate-functions"></a>Агрегатные функции SQL  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие агрегатные функции SQL.  
  
|||||  
|-|-|-|-|  
|Avg|Count|Max|Min|  
|StDev|StDevP|SUM|Var|  
|VarP||||  
  
#### <a name="text-functions"></a>Текстовые функции  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают следующие текстовые функции.  
  
|||||  
|-|-|-|-|  
|Формат|Format$|InStr|InStrRev|  
|LCase|LCase$|Слева|Left$|  
|Len|LTrim|LTrim$|Mid|  
|Mid$|Replace|Right|Right$|  
|RTrim|Пробел|Space$|StrComp|  
|StrConv|Строка|String$|StrReverse|  
|Trim|Trim$|UCase|UCase$|  
  
### <a name="constants"></a>Константы  
 Access не поддерживает в выражениях специальные константы [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] (например, `vbTrue`), поэтому преобразование не требуется. Однако есть одно исключение: ключевое слово `Null` преобразуется в `System.DbNull.Value`.  
  
### <a name="parameters"></a>Параметры  
 При импорте конструктор отчетов просматривает каждое выражение отчета на наличие переменных, которые не соответствуют именам полей и элементам управления. Эти переменные добавляются к параметрам отчета.  
  
 При импорте параметры хранимых процедур всегда преобразуются к строковому типу данных. После импорта отчета необходимо вручную восстановить для параметров нужные типы.  
  
### <a name="object-names"></a>Имена объектов  
 В Access поля могут иметь такое же имя, как элементы управления; в службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] это не так. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 6.0 позволяет использовать пробелы в именах переменных, а Visual Basic .NET — нет. При импорте имена таких объектов заменяются допустимыми именами, а объектам с одинаковыми именами присваиваются уникальные имена. Просматриваются все выражения, и имена переменных, соответствующих переименованным объектам, заменяются новыми именами.  
  
## <a name="rectangles-and-containment"></a>Прямоугольники и включение  
 В определении отчета служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] прямоугольники могут содержать другие элементы отчета. Любой прямоугольник, превышающий размеры элемента отчета и перекрывающий более 90% его поверхности, становится контейнером этого элемента.  
  
## <a name="bitmaps"></a>Битовые карты  
 Все битовые карты, внедренные в отчет, преобразуются при импорте в формат BMP, независимо от первоначального формата. Например, если отчет содержит файлы в формате JPG или GIF, то ресурсы, импортированные вместе с отчетом, будут преобразованы в BMP-файлы. Битовые карты хранятся в отчете в виде внедренных изображений. Дополнительные сведения о внедренных образах см. в разделе [images &#40;построитель отчетов and SSRS&#41;](report-design/images-report-builder-and-ssrs.md).  
  
## <a name="other-considerations"></a>Другие вопросы  
 Дополнительно к приведенным выше сведениям при импорте отчетов Access необходимо учитывать следующие замечания.  
  
-   Условное форматирование не преобразуется.  
  
-   Поле описания в свойствах отчета Access не преобразуется.  
  
  

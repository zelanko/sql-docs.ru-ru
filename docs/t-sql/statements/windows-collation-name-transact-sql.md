---
title: Имя параметров сортировки Windows (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Windows collations [SQL Server]
- names [SQL Server], collations
- collations [SQL Server], Windows collations
- Collation Designator
ms.assetid: acceef84-2c68-46e2-a021-be019b7ab14e
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 84f0a0567996546009bd47e95f51201ffa958de3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847072"
---
# <a name="windows-collation-name-transact-sql"></a>Имя параметров сортировки Windows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Задает имя параметров сортировки Windows с помощью предложения COLLATE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Имя параметра сортировки Windows состоит из двух частей: обозначения параметров сортировки и стиля сравнения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Windows_collation_name> :: =   
CollationDesignator_<ComparisonStyle>  
  
<ComparisonStyle> :: =   
{ CaseSensitivity_AccentSensitivity  [ _KanatypeSensitive ] [ _WidthSensitive ]    
}  
| { _BIN | _BIN2 }  
```  
  
## <a name="arguments"></a>Аргументы  
 *CollationDesignator*  
 Указывает базовые параметры сортировки, используемые параметрами сортировки Windows. Правила базовых параметров сортировки отвечают за следующее.  
  
-   Правила сортировки, применяемые, когда определена словарная сортировка. Правила сортировки основаны на алфавите или языке.  
  
-   Кодовую страницу, используемую для хранения символьных данных не в Юникоде.  
  
 Некоторые примеры.  
  
-   Latin1_General или French: обе используют кодовую страницу 1252.  
  
-   Turkish: использует кодовую страницу 1254.  
  
 *CaseSensitivity*  
 **CI** указывает, что регистр символов не учитывается, **CS** определяет учет регистра.  
  
 *AccentSensitivity*  
 **AI** означает, что диакритические знаки пропускаются, **AS** показывает, что они учитываются.  
  
 *KanatypeSensitive*  
 **Omitted** определяет порядок следования без учета типов японской азбуки, **KS** определяет порядок следования, учитывающий тип японской азбуки.  
  
 *WidthSensitivity*  
 **Omitted** определяет нечувствительность к ширине символов, **WS** определяет чувствительность к ширине символов.  
  
 **BIN**  
 Указывает подлежащий использованию двоичный порядок сортировки, применяющийся для обеспечения обратной совместимости.  
  
 **BIN2**  
 Определяет двоичный порядок сортировки, использующий семантику сравнения кодовых точек.  
  
## <a name="remarks"></a>Remarks  
 В зависимости от версии сортировки, некоторые кодовые точки могут быть не определены. Например, сравните:  
  
```  
SELECT LOWER(nchar(504) COLLATE Latin1_General_CI_AS);   
SELECT LOWER (nchar(504) COLLATE Latin1_General_100_CI_AS);  
GO  
```  
  
 Первая линия возвращает символ верхнего регистра, когда сортировка имеет вид Latin1_General_CI_AS, потому что данная кодовая точка является неопределенной в данной сортировке.  
  
 При работе с некоторыми языками, может быть крайне необходимым избегать прошлых сортировок. Например, это является верным для Telegu.  
  
 В некоторых случаях сортировки Windows и сортировки службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут создать разные планы запросов для одного и того же запроса.  
  
## <a name="examples"></a>Примеры  
 Ниже приведены некоторые примеры имен параметров сортировки Windows.  
  
-   **Latin1_General_100_**  
  
 Параметры сортировки используют правила сортировки словаря Latin1 General, кодовую страницу 1252. Без учета регистра, с учетом диакритических знаков. Параметры сортировки используют правила сортировки словаря Latin1 General и ставят в соответствие кодовую страницу 1252. Показывает номер версии параметров сортировки, если это параметры сортировки Windows: _90 или _100. Без учета регистра (CI), с учетом диакритических знаков (AS).  
  
-   **Estonian_CS_AS**  
  
     Параметры сортировки используют правила сортировки словаря Estonian, кодовую страницу 1257. С учетом регистра, с учетом диакритических знаков.  
  
-   **Latin1_General_BIN**  
  
     Параметры сортировки используют кодовую страницу 1252 и правила двоичной сортировки. Правила сортировки словаря Latin1 General не учитываются.  
  
## <a name="windows-collations"></a>Параметры сортировки Windows  
 Чтобы сформировать список параметров сортировки Windows, которые поддерживаются экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните следующий запрос.  
  
```  
SELECT * FROM sys.fn_helpcollations() WHERE name NOT LIKE 'SQL%';  
```  
  
 В следующей таблице приведены все параметры сортировки Windows, поддерживаемые в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Локаль Windows|Версия параметров сортировки 100|Версия параметров сортировки 90|  
|--------------------|---------------------------|--------------------------|  
|Эльзасский (Франция)|Latin1_General_100_|Недоступно|  
|Амхарик (Эфиопия)|Latin1_General_100_|Недоступно|  
|Армянский (Армения)|Cyrillic_General_100_|Недоступно|  
|Ассамский (Индия)|Assamese_100_ <sup>1</sup>|Недоступно|  
|Башкирский (Россия)|Bashkir_100_|Недоступно|  
|Баскский|Latin1_General_100_|Недоступно|  
|Бенгальский (Бангладеш)|Bengali_100_<sup>1</sup>|Недоступно|  
|Bengali (India)|Bengali_100_<sup>1</sup>|Недоступно|  
|Боснийский (Босния и Герцеговина, кириллица)|Bosnian_Cyrillic_100_|Недоступно|  
|Боснийский (Босния и Герцеговина, латиница)|Bosnian_Latin_100_|Недоступно|  
|Бретонский (Франция)|Breton_100_|Недоступно|  
|Chinese (Macao SAR)|Chinese_Traditional_Pinyin_100_|Недоступно|  
|Chinese (Macao SAR)|Chinese_Traditional_Stroke_Order_100_|Недоступно|  
|Chinese (Singapore)|Chinese_Simplified_Stroke_Order_100_|Недоступно|  
|Корсиканский (Франция)|Corsican_100_|Недоступно|  
|Хорватский (Босния и Герцеговина, латиница)|Croatian_100_|Недоступно|  
|Дари (Афганистан)|Dari_100_|Недоступно|  
|Английский (Индия)|Latin1_General_100_|Недоступно|  
|Английский (Малайзия)|Latin1_General_100_|Недоступно|  
|Английский (Сингапур)|Latin1_General_100_|Недоступно|  
|Филиппинский (Филиппины)|Latin1_General_100_|Недоступно|  
|Фризский (Нидерланды)|Frisian_100_|Недоступно|  
|Грузинский (Грузия)|Cyrillic_General_100_|Недоступно|  
|Гренландский (Гренландия)|Danish_Greenlandic_100_|Недоступно|  
|Гуджарати (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Хауса (Нигерия, латиница)|Latin1_General_100_|Недоступно|  
|Хинди (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Игбо (Нигерия)|Latin1_General_100_|Недоступно|  
|Инуитский (Канада, латиница)|Latin1_General_100_|Недоступно|  
|Инуитский (Канада)|Latin1_General_100_|Недоступно|  
|Ирландский (Ирландия)|Latin1_General_100_|Недоступно|  
|Японский (Япония)|Japanese_XJIS_100_|Japanese_90_, Japanese_|  
|Японский (Япония)|Japanese_Bushu_Kakusu_100_|Недоступно|  
|Каннада (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Кхмерский (Камбоджа)|Khmer_100_<sup>1</sup>|Недоступно|  
|Киче (Гватемала)|Modern_Spanish_100_|Недоступно|  
|Киньяруанда (Руанда)|Latin1_General_100_|Недоступно|  
|Конкани (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Лаосский (Лаосская Народно-Демократическая Республика)|Lao_100_<sup>1</sup>|Недоступно|  
|Нижний Сорбский (Германия)|Latin1_General_100_|Недоступно|  
|Люксембургский (Люксембург)|Latin1_General_100_|Недоступно|  
|Малайялам (Индия)|Indic_General_100_<sup>1</sup>|Недоступно|  
|Мальтийский (Мальта)|Maltese_100_|Недоступно|  
|Маорийский (Новая Зеландия)|Maori_100_|Недоступно|  
|Мапудунгун (Чили)|Mapudungan_100_|Недоступно|  
|Маратхи (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Могавк (Канада)|Mohawk_100_|Недоступно|  
|Монгольский (КНР)|Cyrillic_General_100_|Недоступно|  
|Непальский (Непал)|Nepali_100_<sup>1</sup>|Недоступно|  
|Норвежский (букмол, Норвегия)|Norwegian_100_|Недоступно|  
|Норвежский (нюнорск/ландсмол, Норвегия)|Norwegian_100_|Недоступно|  
|Окситанский (Франция)|French_100_|Недоступно|  
|Ория (Индия)|Indic_General_100_<sup>1</sup>|Недоступно|  
|Пушту (Афганистан)|Pashto_100_<sup>1</sup>|Недоступно|  
|Персидский (Иран)|Persian_100_|Недоступно|  
|Панджабский (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Кечуа (Боливия)|Latin1_General_100_|Недоступно|  
|Кечуа (Эквадор)|Latin1_General_100_|Недоступно|  
|Кечуа (Перу)|Latin1_General_100_|Недоступно|  
|Романш (Швейцария)|Romansh_100_|Недоступно|  
|Саамский (Инари, Финляндия)|Sami_Sweden_Finland_100_|Недоступно|  
|Саамский (Луле, Норвегия)|Sami_Norway_100_|Недоступно|  
|Саамский (Луле, Швеция)|Sami_Sweden_Finland_100_|Недоступно|  
|Саамский (Северный, Финляндия)|Sami_Sweden_Finland_100_|Недоступно|  
|Саамский (Северный, Норвегия)|Sami_Norway_100_|Недоступно|  
|Саамский (Северный, Швеция)|Sami_Sweden_Finland_100_|Недоступно|  
|Саамский (Скольт, Финляндия)|Sami_Sweden_Finland_100_|Недоступно|  
|Саамский (Южный, Норвегия)|Sami_Norway_100_|Недоступно|  
|Саамский (Южный, Швеция)|Sami_Sweden_Finland_100_|Недоступно|  
|Санскрит (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Сербский (Босния и Герцеговина, кириллица)|Serbian_Cyrillic_100_|Недоступно|  
|Сербский (Босния и Герцеговина, латиница)|Serbian_Latin_100_|Недоступно|  
|Сербский (Сербия, кириллица)|Serbian_Cyrillic_100_|Недоступно|  
|Сербский (Сербия, латиница)|Serbian_Latin_100_|Недоступно|  
|Сесуто са Лебоа/Северный Суто (Южная Африка)|Latin1_General_100_|Недоступно|  
|Сетсвана/Тсвана (Южная Африка)|Latin1_General_100_|Недоступно|  
|Синхала (Шри-Ланка)|Indic_General_100_<sup>1</sup>|Недоступно|  
|Суахили (Кения)|Latin1_General_100_|Недоступно|  
|Сирийский (Сирия)|Syriac_100_<sup>1</sup>|Syriac_90_|  
|Таджикский (Таджикистан)|Cyrillic_General_100_|Недоступно|  
|Тамазихт (Алжир, латиница)|Tamazight_100_|Недоступно|  
|Тамильский (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Телугу (Индия)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|Тибетский (КНР)|Tibetan_100_<sup>1</sup>|Недоступно|  
|Туркменский (Туркменистан)|Turkmen_100_|Недоступно|  
|Уйгурский (КНР)|Uighur_100_|Недоступно|  
|Верхний Сорбский (Германия)|Upper_Sorbian_100_|Недоступно|  
|Урду (Пакистан)|Urdu_100_|Недоступно|  
|Валлийский (Великобритания)|Welsh_100_|Недоступно|  
|Волоф (Сенегал)|French_100_|Недоступно|  
|Коса/исиКоса (Южная Африка)|Latin1_General_100_|Недоступно|  
|Якутский (Россия)|Yakut_100_|Недоступно|  
|Носу (КНР)|Latin1_General_100_|Недоступно|  
|Йоруба (Нигерия)|Latin1_General_100_|Недоступно|  
|Зулу/исиЗулу (Южная Африка)|Latin1_General_100_|Недоступно|  
|Устарело. Отсутствует на уровне сервера в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях|Hindi|Hindi|  
|Устарело. Отсутствует на уровне сервера в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях|Korean_Wansung_Unicode|Korean_Wansung_Unicode|  
|Устарело. Отсутствует на уровне сервера в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях|Lithuanian_Classic|Lithuanian_Classic|  
|Устарело. Отсутствует на уровне сервера в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях|Macedonian|Macedonian|  
  
 <sup>1</sup> Параметры сортировки Windows "Только для Юникода" можно применять только к данным на уровне столбца или уровне выражения. Они не могут использоваться в качестве параметров сортировки базы данных или сервера.  
  
 <sup>2</sup> Как и при параметрах сортировки в китайском (Тайвань), в китайском (Макао) используются правила упрощенного китайского языка, но в отличие от китайского (Тайвань) используется кодовая страница 950.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [Константы (Transact-SQL)](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlserver)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [table (Transact-SQL)](../../t-sql/data-types/table-transact-sql.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)  
  
  

---
title: "Набор строк DMSCHEMA_MINING_COLUMNS | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_COLUMNS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_COLUMNS rowset
ms.assetid: ae35ccde-4438-46f4-8611-40b2b1a42fce
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e37841617289eaa71af4d7c2c091459f32a745b6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="dmschemaminingcolumns-rowset"></a>Набор строк DMSCHEMA_MINING_COLUMNS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Описывает отдельные столбцы всех моделей интеллектуального анализа данных в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Этот набор строк ограничивается текущим каталогом.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DMSCHEMA_MINING_COLUMNS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Имя каталога. Заполняется именем базы данных, элементом которой является модель.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Неполное имя схемы. Этот столбец не поддерживается [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Имя модели интеллектуального анализа данных. Этот столбец содержит имя модели интеллектуального анализа данных, с которой связан столбец, и никогда не бывает пустым.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|Имя столбца.|  
|**COLUMN_GUID**|**DBTYPE_GUID**|Идентификатор GUID столбца. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**COLUMN_PROPID**|**DBTYPE_UI4**|Идентификатор свойства столбца. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**|Порядковый номер позиции столбца. Столбцы нумеруются начиная с 1. Этот столбец содержит значение **NULL** , если отсутствует какой-либо постоянный порядковый номер для столбца.|  
|**COLUMN_HAS_DEFAULT**|**DBTYPE_BOOL**|Логическое значение, которое указывает, имеет ли столбец значение по умолчанию.<br /><br /> Значение**TRUE** , если столбец имеет значение по умолчанию, в противном случае — **FALSE**.|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**|Значение по умолчанию для столбца.<br /><br /> Если значением по умолчанию является значение **NULL** , то **COLUMN_HASDEFAULT** содержит **TRUE**, а этот столбец содержит **NULL**.|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**|Битовая маска, которая описывает характеристики столбца. Перечислимый тип **DBCOLUMNFLAGS** задает биты в битовой маске. Этот столбец никогда не бывает пустым.|  
|**IS_NULLABLE**|**DBTYPE_BOOL**|Логическое значение, которое указывает, допускает ли столбец значения NULL.<br /><br /> Значение**FALSE** , если известно, что столбец не допускает значения NULL; **TRUE**в противном случае.|  
|**ТИП ДАННЫХ**|**DBTYPE_UI2**|Признак типа данных столбца. В следующем списке показаны примеры типов возвращаемого признака:<br /><br /> "**TABLE**" возвратит значение **DBTYPE_HCHAPTER**.<br /><br /> "**TEXT**" возвратит значение **DBTYPE_WCHAR**.<br /><br /> "**LONG**" возвратит значение **DBTYPE_I8**.<br /><br /> "**DOUBLE**" возвратит значение **DBTYPE_R8**.<br /><br /> "**DATE**" возвратит значение **DBTYPE_DATE**.|  
|**TYPE_GUID**|**DBTYPE_GUID**|Идентификатор GUID для типа данных столбца. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **VT_NULL**.|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**|Максимально допустимая длина значения данного столбца. Для символьных, двоичных и битовых столбцов это одно из следующих значений.<br /><br /> Максимальная длина столбца в символах, байтах или битах, соответствующая типу столбца, если длина определена. Например, столбец **CHAR(5)** в таблице SQL Server имеет максимальную длину в 5 символов.<br /><br /> Максимальная длина типа данных в символах, байтах или битах, соответствующая типу столбца, если столбец не имеет определенной длины.<br /><br /> Ноль (0), если ни для столбца, ни для типа данных не определена максимальная длина.<br /><br /> Значение**NULL** для всех других типов столбцов.|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**|Максимальная длина столбца в октетах (байтах), если столбец имеет символьный или двоичный тип. Нулевое значение (0) означает, что для столбца не задана максимальная длина. Этот столбец содержит значение **NULL** для всех других типов столбцов.|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**|Максимальная точность столбца, если тип данных столбца представляет собой числовой тип данных, отличный от **VARNUMERIC**.<br /><br /> Значение**NULL** , если тип данных столбца не является числовым или представляет собой **VARNUMERIC**.<br /><br /> Точность столбцов с типом данных **DBTYPE_DECIMAL** или **DBTYPE_NUMERIC** зависит от определения столбца.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**|Число цифр справа от десятичного разделителя, если индикатор типа столбца имеет значение **DBTYPE_DECIMAL**, **DBTYPE_NUMERIC**или **DBTYPE_VARNUMERIC**. В противном случае этот столбец содержит значение **VT_NULL**.|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**|Точность даты-времени (количество цифр в части с обозначением долей секунды) столбца, если типом данных столбца является DateTime или тип интервала; **NULL**в противном случае.|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**|Имя каталога, в котором определена кодировка. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**|Имя схемы с неполным именем, в которой определена кодировка. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**|Имя кодировки. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**|Имя каталога, в котором определены параметры сортировки. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**|Имя схемы с неполным именем, в которой определены параметры сортировки. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**COLLATION_NAME**|**DBTYPE_WSTR**|Имя параметров сортировки. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**|Имя каталога, в котором определен домен. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**|Имя схемы с неполным именем, в которой определен домен. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**ИМЯ_ДОМЕНА**|**DBTYPE_WSTR**|Имя домена. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Понятное описание столбца этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**DISTRIBUTION_FLAG**|**DBTYPE_WSTR**|Описание статистического распределения столбца. Этот столбец содержит одно из следующих значений:<br /><br /> «**ОБЫЧНЫЙ**»<br /><br /> «**LOG_NORMAL**»<br /><br /> «**УНИВЕРСАЛЬНЫЙ**»|  
|**УКАЗЫВАЕТСЯ**|**DBTYPE_WSTR**|Описание содержимого столбца. Этот столбец содержит одно из следующих значений:<br /><br /> «**КЛЮЧ**»<br /><br /> «**DISCRETE**»<br /><br /> «**CONTINUOUS**»<br /><br /> «**DISCRETIZED (**[аргументы]**)**»<br /><br /> «**ORDERED**»<br /><br /> «**КЛЮЧЕВОЙ СТОЛБЕЦ ВРЕМЕНИ**»<br /><br /> «**CYCLICAL**»<br /><br /> «**ВЕРОЯТНОСТЬ**»<br /><br /> «**ДИСПЕРСИЮ**»<br /><br /> «**STDEV**»<br /><br /> «**ПОДДЕРЖКИ**»<br /><br /> «**PROBABILITY_VARIANCE**»<br /><br /> «**PROBABILITY_STDEV**»<br /><br /> «**"KEY SEQUENCE**»|  
|**MODELING_FLAG**|**DBTYPE_WSTR**|Разделенный запятыми список флагов. Определены следующие флаги:<br /><br /> «**MODEL_EXISTENCE_ONLY**»<br /><br /> «**РЕГРЕССОРА**»<br /><br /> Зависящие от алгоритма флаги моделирования могут также содержаться в этом столбце.|  
|**IS_RELATED_TO_KEY**|**DBTYPE_BOOL**|Логическое значение, которое указывает, связан ли столбец с ключом.<br /><br /> Значение**TRUE** , если этот столбец связан с ключом. Если ключ состоит из единственного столбца, то в поле **RELATED_ATTRIBUTE** может дополнительно содержаться имя этого столбца.|  
|**RELATED_ATTRIBUTE**|**DBTYPE_WSTR**|Имя целевого столбца, с которым связан текущий столбец или представляет для него специальное свойство.|  
|**IS_INPUT**|**DBTYPE_BOOL**|Логическое значение, которое указывает, является ли столбец входным столбцом.<br /><br /> Значение**VARIANT_TRUE** , если столбец является входным.|  
|**IS_PREDICTABLE**|**DBTYPE_BOOL**|Логическое значение, которое указывает, является ли столбец прогнозируемым.<br /><br /> Значение**TRUE** , если столбец является прогнозируемым.|  
|**CONTAINING_COLUMN**|**DBTYPE_WSTR**|Имя столбца **TABLE** , который содержит этот столбец. Этот столбец содержит значение **NULL** , если столбец не содержится в другом столбце.|  
|**PREDICTION_SCALAR_FUNCTIONS**|**DBTYPE_WSTR**|Разделенный запятыми список скалярных функций, которые могут быть выполнены применительно к столбцу.|  
|**PREDICTION_TABLE_FUNCTIONS**|**DBTYPE_WSTR**|Разделенный запятыми список функций, которые могут быть применены к столбцу. Функции должны возвращать таблицу. Этот список имеет следующий формат:<br /><br /> `<function name>(<column1> [, <column2>], ...)`<br /><br /> Этот формат обеспечивает для клиентского приложения возможность определять подпись (список параметров) для соответствующей функции.|  
|**IS_POPULATED**|**DBTYPE_BOOL**|Логическое значение, которое указывает, было ли выполнено обучение столбца с помощью набора возможных значений.<br /><br /> Значение**TRUE** , если обучение столбца с помощью набора возможных значений было выполнено.<br /><br /> Содержит **FALSE** , если столбец не заполнен.|  
|**PREDICTION_SCORE**|**DBTYPE_R8**|Оценка модели после прогнозирования столбца. Оценка используется для измерения точности модели.|  
|**SOURCE_COLUMN**|**DBTYPE_WSTR**|Имя исходного столбца структуры интеллектуального анализа данных для текущего столбца интеллектуального анализа.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DMSCHEMA_MINING_COLUMNS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

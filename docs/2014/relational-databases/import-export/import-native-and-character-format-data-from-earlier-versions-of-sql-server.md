---
title: Импорт данных в собственном и символьном формате из предыдущих версий SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- earlier versions [SQL Server], import and export data formats
- -V switch
- data formats [SQL Server], earlier versions
- previous versions [SQL Server], import and export data formats
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a87863d3046de695e489e83ec46eb073a7f4761c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62745924"
---
# <a name="import-native-and-character-format-data-from-earlier-versions-of-sql-server"></a>Импорт данных в собственном и символьном формате из предыдущих версий SQL Server
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]можно с помощью программы **bcp** импортировать данные в собственном и символьном формате из [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , задав ключ **-V** . Ключ **-V** указывает [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , что следует использовать типы данных из указанной более ранней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и что формат файла данных аналогичен формату в предыдущей версии.  
  
 Чтобы задать более раннюю версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для файла данных, используйте параметр **-V** с одним из следующих квалификаторов:  
  
|Версия SQL Server|Квалификатор|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|**-V80**|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|**-V90**|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|**-V100**|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|**-V 110**|  
  
## <a name="interpretation-of-data-types"></a>Интерпретация типов данных  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях была добавлена поддержка некоторых новых типов данных. Если нужно импортировать новый тип данных в более раннюю версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , эти данные необходимо сохранить в формате, который могут прочитать старые клиенты **bcp** . Следующая таблица содержит сведения о том, как новые типы данных преобразуются для совместимости с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Новые типы данных в SQL Server 2005|Совместимые типы данных в версии 6*x*|Совместимые типы данных в версии 70|Совместимые типы данных в версии 80|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|`bigint`|`decimal`|`decimal`|*|  
|`sql_variant`|`text`|`nvarchar(4000)`|*|  
|`varchar(max)`|`text`|`text`|`text`|  
|`nvarchar(max)`|`ntext`|`ntext`|`ntext`|  
|`varbinary(max)`|`image`|`image`|`image`|  
|XML|`ntext`|`ntext`|`ntext`|  
|ОПРЕДЕЛЯЕМЫЙ ПОЛЬЗОВАТЕЛЕМ ТИП<sup>1</sup>|`image`|`image`|`image`|  
  
 \* Этот тип поддерживается изначально.  
  
 <sup>1</sup> UDT обозначает определяемый пользователем тип.  
  
## <a name="exporting-using--v-80"></a>Экспорт с ключом -V 80  
 При массовом экспорте данных с помощью **-V80** переключиться, `nvarchar(max)`, `varchar(max)`, `varbinary(max)`, XML и определяемый пользователем тип данных в собственном режиме хранятся с 4-байтовым префиксом, как `text`, `image`и `ntext`данных, вместо 8-байтового префикса, используемого по умолчанию для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий.  
  
## <a name="copying-date-values"></a>Копирование значений данных  
 Программа**bcp** использует API-интерфейс массового копирования ODBC. Таким образом, для импорта значений дат в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]программа **bcp** использует формат данных ODBC (*гггг-мм-дд чч:мм:сс*[*.f...*]).  
  
 **Bcp** команда экспортирует файлы данных символьного формата с помощью формата ODBC по умолчанию для `datetime` и `smalldatetime` значения. Например, столбец типа `datetime`, содержащий дату `12 Aug 1998`, копируется с помощью массового копирования в файл данных в качестве строки символов `1998-08-12 00:00:00.000`.  
  
> [!IMPORTANT]  
>  При импорте данных в `smalldatetime` поле с помощью **bcp**, убедитесь, что значение секунд равно 00,000; в противном случае операция завершится ошибкой. Тип данных `smalldatetime` содержит значения только с точностью до минуты. В данном случае инструкции BULK INSERT и INSERT ... SELECT * FROM OPENROWSET(BULK...) не приведут к ошибке, но усекут значение секунд.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Использование форматов данных для массового импорта или экспорта**  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a>См. также:  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)   
 [Обратная совместимость компонента SQL Server Database Engine](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Функции CAST и CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  

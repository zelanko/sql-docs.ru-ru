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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f41e323faeb898be1f44159760bb1c28b7ab024
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011919"
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
|Определяемый пользователем тип<sup>1</sup>|`image`|`image`|`image`|  
  
 \*Этот тип поддерживается изначально.  
  
 <sup>1</sup> UDT обозначает определяемый пользователем тип.  
  
## <a name="exporting-using--v-80"></a>Экспорт с ключом -V 80  
 При выполнении операций с массовым экспортом `varbinary(max)`с помощью параметра `text` `image` `ntext` [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `nvarchar(max)` `varchar(max)` **-V80** данные,,, XML и определяемые пользователем типы данных в собственном режиме сохраняются с помощью 4-байтного префикса, например, и данных, вместо 8-байтного префикса по умолчанию для и более поздних версий.  
  
## <a name="copying-date-values"></a>Копирование значений данных  
 Программа **bcp** использует API-интерфейс для выполнения операций с массовым копированием ODBC. Таким образом, для импорта значений дат в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]программа **bcp** использует формат данных ODBC (*гггг-мм-дд чч:мм:сс*[*.f...*]).  
  
 Команда **bcp** экспортирует файлы данных символьного формата, используя формат ODBC по `datetime` умолчанию `smalldatetime` для значений и. Например, столбец типа `datetime`, содержащий дату `12 Aug 1998`, копируется с помощью массового копирования в файл данных в качестве строки символов `1998-08-12 00:00:00.000`.  
  
> [!IMPORTANT]  
>  При импорте данных в `smalldatetime` поле с помощью программы **bcp**убедитесь, что значение для секунд равно 00,000; в противном случае операция завершится ошибкой. Тип данных `smalldatetime` содержит значения только с точностью до минуты. В данном случае инструкции BULK INSERT и INSERT ... SELECT * FROM OPENROWSET(BULK...) не приведут к ошибке, но усекут значение секунд.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Использование форматов данных для массового импорта или экспорта**  
  
-   [Используйте символьный формат для импорта или экспорта &#40;данных SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте собственный формат для импорта или экспорта &#40;данных SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте символьный формат Юникода для импорта или экспорта &#40;данных SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте собственный формат Юникода для импорта или экспорта &#40;данных SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a>См. также:  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Типы данных &#40;&#41;Transact-SQL](/sql/t-sql/data-types/data-types-transact-sql)   
 [SQL Server ядро СУБД обратной совместимости](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Функции CAST и CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  

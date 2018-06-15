---
title: Параметры команд | Документы Microsoft
description: Параметры команды
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, parameters
- OLE DB Driver for SQL Server, commands
- parameters [OLE DB Driver for SQL Server], OLE DB
- commands [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 79cfcfc713b774c8f60055971e7aba07de9c18c8
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305923"
---
# <a name="command-parameters"></a>Параметры команд
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Параметры помечаются в тексте команды знаками вопроса. Например, следующая инструкция SQL помечена для одного входного параметра:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Для повышения производительности путем уменьшения сетевого трафика, драйвер OLE DB для SQL Server не является производным автоматически сведения о параметрах Если **ICommandWithParameters::GetParameterInfo** или **ICommandPrepare:: Подготовка** вызывается перед выполнением команды. Это означает, что драйвер OLE DB для SQL Server не автоматически.  
  
-   Проверьте правильность типа данных, указанного с **ICommandWithParameters::SetParameterInfo**.  
  
-   не сопоставляет тип DBTYPE, указанный в данных привязки метода доступа, с правильным типом данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для параметра.  
  
 Приложения будут получать возможные ошибки или потери точности одним из этих методов, если они указывают типы данных, несовместимые с типом данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для параметра.  
  
 Чтобы гарантировать, что подобная ситуация не произойдет, для приложения необходимо:  
  
-   Убедитесь, что *pwszDataSourceType* соответствует [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных для параметра жестко запрограммированного **ICommandWithParameters::SetParameterInfo**.  
  
-   Проверить, что тип значения DBTYPE, связанного с параметром, совпадает с типом данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для жестко запрограммированного метода доступа.  
  
-   Код приложения для вызова **ICommandWithParameters::GetParameterInfo** , чтобы поставщик можно получить [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типы данных параметров динамически. Обратите внимание, что это приведет к дополнительному обмену данными с сервером.  
  
> [!NOTE]  
>  Поставщик не поддерживает вызов **ICommandWithParameters::GetParameterInfo** для любого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] инструкции UPDATE или DELETE, содержащей предложение FROM; для любой инструкции SQL, в зависимости от вложенного запроса, содержащего параметры; для инструкций SQL, содержащих маркеры параметров в обоих выражениях сравнение, like или количественные предиката; или запросы, в которых один из параметров является параметром функции. При обработке пакета инструкций SQL, поставщик также не поддерживает вызов метода **ICommandWithParameters::GetParameterInfo** для маркеров параметров в инструкциях после первой инструкцией в пакете. Комментарии (/ * \*/) не разрешены в [!INCLUDE[tsql](../../../includes/tsql-md.md)] команды.  
  
 Драйвер OLE DB для SQL Server поддерживает входные параметры в командах инструкций SQL. Для команд вызова процедур драйвер OLE DB для SQL Server поддерживает вход, выход и входных/выходных параметров. Значения выходных параметров возвращаются приложению либо при выполнении (только если не возвращаются наборы строк), либо когда все возвращаемые наборы строк уже использованы приложением. Чтобы убедиться, что возвращенные значения являются допустимыми, используйте **IMultipleResults** для принудительного потребления набора строк.  
  
 Имена параметров хранимых процедур не обязательно указывать в структуре DBPARAMBINDINFO. Используйте NULL для значения *pwszName* элемент, чтобы указать, что драйвер OLE DB для SQL Server должен пропускать имя параметра и использовать только порядковый номер, указанный в *rgParamOrdinals* членом  **ICommandWithParameters::SetParameterInfo**. Если текст команды содержит как именованные, так и неименованные параметры, все неименованные параметры должны быть указаны до именованных параметров.  
  
 Если указано имя параметра хранимой процедуры драйвер OLE DB для SQL Server проверяет имя, убедитесь, что он является допустимым. Драйвер OLE DB для SQL Server возвращает ошибку при получении ошибочного имени параметра от потребителя.  
  
> [!NOTE]  
>  Для предоставления поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML и определяемых пользователем типов (UDT), драйвер OLE DB для SQL Server реализует новый [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Команды](../../oledb/ole-db-commands/commands.md)  
  
  

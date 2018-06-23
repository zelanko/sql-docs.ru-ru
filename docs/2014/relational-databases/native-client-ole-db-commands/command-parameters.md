---
title: Параметры команд | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cf00eb9d28acb7727b888eb065647184653b7e87
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192447"
---
# <a name="command-parameters"></a>Параметры команд
  Параметры помечаются в тексте команды знаками вопроса. Например, следующая инструкция SQL помечена для одного входного параметра:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Для повышения производительности путем уменьшения сетевого трафика, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не является производным автоматически сведения о параметрах Если **ICommandWithParameters::GetParameterInfo** или  **ICommandPrepare::Prepare** вызывается перед выполнением команды. Это означает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не автоматически:  
  
-   Проверьте правильность типа данных, указанного с **ICommandWithParameters::SetParameterInfo**.  
  
-   не сопоставляет тип DBTYPE, указанный в данных привязки метода доступа, с правильным типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметра.  
  
 Приложения будут получать возможные ошибки или потери точности одним из этих методов, если они указывают типы данных, несовместимые с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметра.  
  
 Чтобы гарантировать, что подобная ситуация не произойдет, для приложения необходимо:  
  
-   Убедитесь, что *pwszDataSourceType* соответствует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных для параметра жестко запрограммированного **ICommandWithParameters::SetParameterInfo**.  
  
-   Проверить, что тип значения DBTYPE, связанного с параметром, совпадает с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для жестко запрограммированного метода доступа.  
  
-   Код приложения для вызова **ICommandWithParameters::GetParameterInfo** , чтобы поставщик можно получить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных параметров динамически. Обратите внимание, что это приведет к дополнительному обмену данными с сервером.  
  
> [!NOTE]  
>  Поставщик не поддерживает вызов **ICommandWithParameters::GetParameterInfo** для любого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции UPDATE или DELETE, содержащей предложение FROM; для любой инструкции SQL, в зависимости от вложенного запроса, содержащего параметры; для инструкций SQL, содержащих маркеры параметров в обоих выражениях сравнение, like или количественные предиката; или запросы, в которых один из параметров является параметром функции. При обработке пакета инструкций SQL, поставщик также не поддерживает вызов метода **ICommandWithParameters::GetParameterInfo** для маркеров параметров в инструкциях после первой инструкцией в пакете. Комментарии (/ * \*/) не разрешены в [!INCLUDE[tsql](../../includes/tsql-md.md)] команды.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента поддерживает входные параметры в командах инструкций SQL. Для команд вызова процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента поддерживает вход, выход и входных/выходных параметров. Значения выходных параметров возвращаются приложению либо при выполнении (только если не возвращаются наборы строк), либо когда все возвращаемые наборы строк уже использованы приложением. Чтобы убедиться, что возвращенные значения являются допустимыми, используйте **IMultipleResults** для принудительного потребления набора строк.  
  
 Имена параметров хранимых процедур не обязательно указывать в структуре DBPARAMBINDINFO. Используйте NULL для значения *pwszName* члена, чтобы указать, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента должен пропускать имя параметра и использовать только порядковый номер, указанный в *rgParamOrdinals*членом **ICommandWithParameters::SetParameterInfo**. Если текст команды содержит как именованные, так и неименованные параметры, все неименованные параметры должны быть указаны до именованных параметров.  
  
 Если указано имя параметра хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет имя, убедитесь, что он является допустимым. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку при получении ошибочного имени параметра от потребителя.  
  
> [!NOTE]  
>  Для предоставления поддержки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML и определяемых пользователем типов (UDT), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента реализует новый [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Команды](commands.md)  
  
  
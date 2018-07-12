---
title: Параметры команд | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 37bf1eaf79ad3a26e5a1e19108850af05d276538
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414433"
---
# <a name="command-parameters"></a>Параметры команд
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Параметры помечаются в тексте команды знаками вопроса. Например, следующая инструкция SQL помечена для одного входного параметра:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Для повышения производительности путем уменьшения сетевого трафика, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не является производным автоматически сведения о параметрах Если **ICommandWithParameters::GetParameterInfo** или  **ICommandPrepare::Prepare** вызывается перед выполнением команды. Это означает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не автоматически:  
  
-   Проверьте правильность типа данных, указанного с помощью **ICommandWithParameters::SetParameterInfo**.  
  
-   не сопоставляет тип DBTYPE, указанный в данных привязки метода доступа, с правильным типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметра.  
  
 Приложения будут получать возможные ошибки или потери точности одним из этих методов, если они указывают типы данных, несовместимые с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметра.  
  
 Чтобы гарантировать, что подобная ситуация не произойдет, для приложения необходимо:  
  
-   Убедитесь, что *pwszDataSourceType* соответствует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных для параметра жестко запрограммированного **ICommandWithParameters::SetParameterInfo**.  
  
-   Проверить, что тип значения DBTYPE, связанного с параметром, совпадает с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для жестко запрограммированного метода доступа.  
  
-   Код приложения для вызова **ICommandWithParameters::GetParameterInfo** , чтобы поставщик можно получить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных параметров динамически. Обратите внимание, что это приведет к дополнительному обмену данными с сервером.  
  
> [!NOTE]  
>  Поставщик не поддерживает вызов метода **ICommandWithParameters::GetParameterInfo** для любого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции UPDATE или DELETE, содержащей предложение FROM; для любой инструкции SQL, в зависимости от вложенного запроса, содержащего параметры; для инструкций SQL, содержащих маркеры параметров в обоих выражениях сравнения, например, или в целевых показателях предикату; или запросов, так как один из параметров является параметром функции. При обработке пакета инструкций SQL, поставщик также не поддерживает вызов метода **ICommandWithParameters::GetParameterInfo** для маркеров параметров в выражениях после первой инструкцией в пакете. Комментарии (/ * \*/) не разрешены в [!INCLUDE[tsql](../../includes/tsql-md.md)] команды.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает входные параметры в командах инструкций SQL. Для команд вызова процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента поддерживает входные данные, выходные данные и параметры ввода вывода. Значения выходных параметров возвращаются приложению либо при выполнении (только если не возвращаются наборы строк), либо когда все возвращаемые наборы строк уже использованы приложением. Чтобы убедиться, что возвращаемые значения являются допустимыми, используйте **IMultipleResults** для принудительного потребления набора строк.  
  
 Имена параметров хранимых процедур не обязательно указывать в структуре DBPARAMBINDINFO. Используйте NULL для значения *pwszName* члена, чтобы указать, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента должен пропускать имя параметра и использовать только порядковый номер, указанный в *rgParamOrdinals*членом **ICommandWithParameters::SetParameterInfo**. Если текст команды содержит как именованные, так и неименованные параметры, все неименованные параметры должны быть указаны до именованных параметров.  
  
 Если указано имя параметра хранимой процедуры, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет имя, чтобы убедиться, что он является допустимым. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку при получении ошибочного имени параметра от потребителя.  
  
> [!NOTE]  
>  Для предоставления поддержки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML и определяемых пользователем типов (UDT), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента реализует новый [ISSCommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Команды](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  

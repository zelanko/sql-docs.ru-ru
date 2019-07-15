---
title: Связь запроса с подключением в проекте | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], query associations
- projects [SQL Server Management Studio], connections
- projects [SQL Server Management Studio], query connections
- query associations [SQL Server Management Studio]
ms.assetid: c9625ae0-29c1-4179-a709-51b7e2f9e23d
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 4b455fee7632f243493a85baf81950b48135f889
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67683122"
---
# <a name="associate-a-query-with-a-connection-in-a-project"></a>Связь запроса с соединением в проекте
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Если запрос был создан без соединения или если запрос был перемещен из одного проекта в другой, он не будет связан с соединением в текущем проекте.  
  
### <a name="to-associate-a-query-with-a-connection-in-a-project"></a>Связывание запроса с соединением в проекте  
  
1.  Если запрос открыт в редакторе запросов, щелкните правой кнопкой мыши в пустой области редактора запросов и в контекстном меню укажите **Соединение**, а затем **Соединить**. Если запрос не открыт, для соединения запроса дважды щелкните запрос в обозревателе решений.  
  
2.  В диалоговом окне **Подключиться к ядру СУБД** введите сведения о соединении. Если они совпадут с существующим соединением, запрос будет связан с этим соединением.  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Изменение соединение, связанное с запросом](../../ssms/solution/change-the-connection-associated-with-a-query.md)  
[Просмотр или изменение свойств соединения в проекте](../../ssms/solution/view-or-change-the-properties-of-a-connection-in-a-project.md)  
  

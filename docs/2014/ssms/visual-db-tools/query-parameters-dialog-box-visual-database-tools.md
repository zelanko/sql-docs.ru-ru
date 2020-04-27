---
title: Диалоговое окно "Параметры запроса" (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 61707b6ca955ee137cbbc93a6a108dc3930e1b12
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63010681"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Диалоговое окно «Параметры запроса» (визуальные инструменты для баз данных)
  Данное диалоговое окно позволяет вводить значения для параметров, определенных в запросе. Это диалоговое окно появляется при выполнении запроса, содержащего параметры, которые должны быть введены конечным пользователем во время запуска.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Список параметров, определенных для выполняемого запроса. Если запрос содержит именованные параметры, то имена отобразятся в списке. Если запрос содержит неименованные параметры, то для каждого параметра запроса в списке будут приведены имена параметров, определенные системой.  
  
 **Value**  
 Введите значение для каждого параметра, приведенного в списке **Имя**. Значение, использованное в последний раз, будет отображено в качестве значения параметра по умолчанию.  
  
## <a name="example"></a>Пример  
 Следующий запрос на панели SQL открывает диалоговое окно «Параметры запроса» при выполнении в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>См. также:  
 [Запрос с параметрами (визуальные инструменты для баз данных)](visual-database-tools.md)  
  
  

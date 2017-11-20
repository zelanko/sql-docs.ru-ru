---
title: "Страница «выражения» | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2517f3b049261614a219d64698a99bd82e14915d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="expressions-page"></a>Страница «Выражения»
  На странице **Выражения** можно изменить выражения свойств и открыть диалоговые окна **Редактор выражений свойств** и **Построитель выражений для свойств** .  
  
 Выражения свойств обновляют значения свойств при выполнении пакета. Выражения свойств можно использовать вместе со свойствами пакетов, задач, контейнеров, диспетчеров соединений, а также с некоторыми компонентами потока данных. Выражения оцениваются, и их результаты используются вместо значений свойств, которые устанавливаются при конфигурации пакета и объектов пакета. Выражения могут включать переменные, а также функции и операторы, предоставляемые языком выражений. К примеру, можно создать строку темы сообщения для задачи «Отправка почты» путем объединения значения переменной, в которой содержится строка «Прогноз погоды на », и возвращаемых результатов функции GETDATE(), чтобы получить строку вида «Прогноз погоды на 4/5/2006».  
  
 Дополнительные сведения о написании выражений и использовании выражений свойств см. в разделах [Выражения служб Integration Services (SSIS)](../../integration-services/expressions/integration-services-ssis-expressions.md) и [Использование выражений свойств в пакетах](../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
## <a name="options"></a>Параметры  
 **Выражения (…)**  
 Нажмите кнопку с многоточием, чтобы открыть диалоговое окно **Редактор выражений свойств** . Дополнительные сведения см. в статье [Property Expressions Editor](../../integration-services/expressions/property-expressions-editor.md).  
  
 **\<Имя свойства >**  
 Нажмите кнопку с многоточием, чтобы открыть диалоговое окно **Построитель выражений** . Дополнительные сведения см. в статье [Expression Builder](../../integration-services/expressions/expression-builder.md).  
  
## <a name="see-also"></a>См. также  
 [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md)   
 [Системные переменные](../../integration-services/system-variables.md)   
 [Службы Integration Services &#40; Службы SSIS &#41; Выражения](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  


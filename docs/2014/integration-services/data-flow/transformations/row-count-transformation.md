---
title: Преобразование "Подсчет строк" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 966f42cf41f93c162ef3aac7be17fce920edbceb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209534"
---
# <a name="row-count-transformation"></a>преобразование «Подсчет строк»
  Преобразование «Подсчет строк» подсчитывает строки по мере прохождения их в потоке данных и сохраняет конечный результат в переменной.  
  
 A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] может обновлять значения переменных, используемых в скриптах, выражениях и выражениях свойств. (Например, переменная, используемая для подсчета строк, может обновить текстовое сообщение электронной почты, добавив количество строк.) Переменная, используемая преобразованием «Подсчет строк», должна существовать и находиться в области задачи потока данных, к которой относится поток данных с преобразованием «Подсчет строк».  
  
 Преобразование сохраняет значение подсчета строк таблицы в переменной только после прохождения последней строки через преобразование. Поэтому значение переменной не обновляется сразу, чтобы использовать обновленное значение в потоке данных, содержащем преобразование «Подсчет строк». Можно использовать обновленную переменную в отдельном потоке данных.  
  
 Это преобразование имеет один вход и один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-row-count-transformation"></a>Настройка преобразования «Подсчет строк»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../../common-properties.md)  
  
-   [Пользовательские свойства преобразований](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services &#40;SSIS&#41; переменных](../../integration-services-ssis-variables.md)   
 [Поток данных](../data-flow.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
  

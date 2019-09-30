---
title: Преобразование "Подсчет строк" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cd1b3a72a91eb3c2a2252eefcec6cf7416cae8f
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297870"
---
# <a name="row-count-transformation"></a>преобразование «Подсчет строк»

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Преобразование «Подсчет строк» подсчитывает строки по мере прохождения их в потоке данных и сохраняет конечный результат в переменной.  
  
 A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] может обновлять значения переменных, используемых в скриптах, выражениях и выражениях свойств. (Например, переменная, используемая для подсчета строк, может обновить текстовое сообщение электронной почты, добавив количество строк.) Переменная, используемая преобразованием «Подсчет строк», должна существовать и находиться в области задачи потока данных, к которой относится поток данных с преобразованием «Подсчет строк».  
  
 Преобразование сохраняет значение подсчета строк таблицы в переменной только после прохождения последней строки через преобразование. Поэтому значение переменной не обновляется сразу, чтобы использовать обновленное значение в потоке данных, содержащем преобразование «Подсчет строк». Можно использовать обновленную переменную в отдельном потоке данных.  
  
 Это преобразование имеет один вход и один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-row-count-transformation"></a>Настройка преобразования «Подсчет строк»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также:  
 [Переменные в службах Integration Services (SSIS)](../../../integration-services/integration-services-ssis-variables.md)   
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  

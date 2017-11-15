---
title: "Автоматическое формирование значений атрибута Code (службы Master Data Services) | Документы Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
caps.latest.revision: "5"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f75fbf0f8ab630615d52ae217566d6b6a8790520
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a>Автоматическое формирование значений атрибута Code (службы Master Data Services)
  Если необходимо автоматически задавать целое число для значения Code при создании нового элемента, то в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]значения для атрибута Code сущности могут формироваться автоматически.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Сущность должна существовать. Дополнительные сведения см. в разделе [Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-automatically-generate-code-values"></a>Автоматическое формирование значений Code  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) в сетке выберите строку для модели, содержащей сущность, которую необходимо изменить, а затем щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) в сетке выберите строку сущности, для которой необходимо создать коды, а затем щелкните **Изменить**.  
  
4.  Установите флажок в поле **Автоматически создавать значения кода** .  
  
5.  В поле **Начать с** введите начальное значение, с которого начнется приращение. Если элементы уже существуют, то значение Code будет установлено, исходя из наибольшего существующего значения. Например, если наибольшее существующее значение Code равно 299, то следующее значение Code элемента будет равно 300.  
  
6.  Нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Автоматическое создание кодов (службы Master Data Services)](../master-data-services/automatic-code-creation-master-data-services.md)   
 [Автоматическое формирование значений атрибута, отличного от Code (службы Master Data Services)](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  

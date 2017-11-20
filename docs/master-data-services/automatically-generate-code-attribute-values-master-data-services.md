---
title: "Автоматическое формирование значений атрибута Code (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
caps.latest.revision: 5
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 02d1b2ab9e23d4bc0ff7a5e3c11b16ef6d26859f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

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
  
  


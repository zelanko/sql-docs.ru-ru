---
title: Автоматическое формирование значений атрибута Code (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a8cfcda0d6fc37db1b620fd64c044e322f81877e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188715"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a>Автоматическое формирование значений атрибута Code (службы Master Data Services)
  Если необходимо автоматически задавать целое число для значения Code при создании нового элемента, то в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]значения для атрибута Code сущности могут формироваться автоматически.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Сущность должна существовать. Дополнительные сведения см. в разделе [Создание сущности (службы Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-automatically-generate-code-values"></a>Автоматическое формирование значений Code  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На **обозревателя моделей** страницы, в строке меню наведите курсор на **управление** и нажмите кнопку **сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, для которой необходимо сформировать коды.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  Установите флажок в поле **Автоматически создавать значения кода** .  
  
7.  В поле **Начать с** введите начальное значение, с которого начнется приращение. Если элементы уже существуют, то значение Code будет установлено, исходя из наибольшего существующего значения. Например, если наибольшее существующее значение Code равно 299, то следующее значение Code элемента будет равно 300.  
  
8.  Нажмите кнопку **сохранить сущность**.  
  
## <a name="see-also"></a>См. также  
 [Автоматическое создание кодов &#40;службы Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)   
 [Автоматическое формирование значений атрибута отличного от Code &#40;службы Master Data Services&#41;](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
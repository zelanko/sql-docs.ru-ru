---
title: Отмена транзакции (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1bc306eda0d7c12bfbb6d7fc32e50189b213c30b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971104"
---
# <a name="reverse-a-transaction-master-data-services"></a>Отмена транзакции (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]администратор может обратить транзакцию, когда необходимо отменить действие. Примеры транзакций: изменения значений атрибутов, перемещение иерархий, удаление элементов.  
  
## <a name="prerequisites"></a>Предварительные условия  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-reverse-a-transaction"></a>Отмена транзакции  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] нажмите **Управление версиями**.  
  
2.  В строке меню выберите пункт **Транзакции**.  
  
3.  На странице **Транзакции** выберите модель в списке **Модель** .  
  
4.  Выберите версию из списка **Версия** .  
  
5.  Щелкните в сетке строку транзакции, которую необходимо отменить.  
  
6.  Нажмите кнопку **Отменить транзакцию**.  
  
7.  В диалоговом окне подтверждения нажмите кнопку **ОК**. В сетку добавляется еще одна транзакция, соответствующая отмененной транзакции.  
  
## <a name="see-also"></a>См. также:  
 [Master Data Services &#40;транзакций&#41;](../../2014/master-data-services/transactions-master-data-services.md)   
 [Повторная активация элемента или коллекции (службы Master Data Services)](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
  
  

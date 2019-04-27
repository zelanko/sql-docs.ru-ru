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
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 24e1c1fea5404d984f05391624fd244960c0eec3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765287"
---
# <a name="reverse-a-transaction-master-data-services"></a>Отмена транзакции (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]администратор может обратить транзакцию, когда необходимо отменить действие. Примеры транзакций: изменения значений атрибутов, перемещение иерархий, удаление элементов.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
### <a name="to-reverse-a-transaction"></a>Отмена транзакции  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] щелкните **Управление версиями**.  
  
2.  В строке меню выберите пункт **Транзакции**.  
  
3.  На странице **Транзакции** выберите модель в списке **Модель** .  
  
4.  Выберите версию из списка **Версия** .  
  
5.  Щелкните в сетке строку транзакции, которую необходимо отменить.  
  
6.  Нажмите кнопку **Отменить транзакцию**.  
  
7.  В диалоговом окне подтверждения нажмите кнопку **ОК**. В сетку добавляется еще одна транзакция, соответствующая отмененной транзакции.  
  
## <a name="see-also"></a>См. также  
 [Транзакции (службы Master Data Services)](../../2014/master-data-services/transactions-master-data-services.md)   
 [Повторная активация элемента или коллекции (службы Master Data Services)](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
  
  

---
title: "Повторная активация элемента или коллекции (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "коллекции [службы Master Data Services], повторная активация"
  - "консолидированные элементы [службы Master Data Services], повторная активация"
  - "повторная активация элементов [службы Master Data Services]"
  - "элементы [службы Master Data Services], повторная активация"
  - "повторная активация коллекций [службы Master Data Services]"
  - "конечные элементы [службы Master Data Services], повторная активация"
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
caps.latest.revision: 11
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Повторная активация элемента или коллекции (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно повторно активировать элемент, который был:  
  
-   деактивирован в промежуточном процессе;  
  
-   удален в MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)];  
  
-   удален в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
 При повторной активации элемента восстанавливаются его атрибуты и членство в иерархиях и коллекциях.  
  
 Также можно повторно активировать коллекции. При этом восстанавливаются атрибуты коллекции и принадлежащие к ней элементы.  
  
 При повторной активации коллекции или элемента восстанавливаются все предыдущие транзакции.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]необходимо иметь разрешение на доступ к функциональной области **Управление версиями** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### Повторная активация элемента или коллекции  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] нажмите **Управление версиями**.  
  
2.  В строке меню выберите пункт **Транзакции**.  
  
3.  На странице **Транзакции** выберите модель в списке **Модель** .  
  
4.  Выберите версию из списка **Версия** .  
  
5.  На панели **Транзакции** щелкните строку элемента или коллекции, которые необходимо повторно активировать. Эта строка должна иметь состояние **Активный** в столбце **Прежнее значение** и **Выключен** в столбце **Новое значение**.  
  
6.  Нажмите кнопку **Отменить транзакцию**.  
  
7.  В диалоговом окне подтверждения нажмите кнопку **ОК**. Будет добавлена новая транзакция со значением **Активный** в столбце **Новое значение** .  
  
## См. также:  
 [Удаление элемента или коллекции (службы Master Data Services)](../master-data-services/delete-a-member-or-collection-master-data-services.md)   
 [Элементы (службы Master Data Services)](../master-data-services/members-master-data-services.md)   
 [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md)  
  
  
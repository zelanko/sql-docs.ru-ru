---
title: "Добавление заметки для транзакции (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: annotations [Master Data Services], for transactions
ms.assetid: f5a6b2ca-56de-4e42-9da8-fba0ac3e8d92
caps.latest.revision: "6"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b21908af85948492677134c17465a6788f3b9b5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="annotate-a-transaction-master-data-services"></a>Добавление заметки для транзакции (Master Data Services)
  Службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]позволяют добавить к транзакции заметку, если необходимо предоставление дополнительных сведений о транзакции для архивных целей.  
  
> [!NOTE]  
>  Заметки нельзя удалить.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Для добавления заметок к созданным транзакциям необходимы права на доступ к функциональной области **Браузер** и как минимум разрешение **Обновление** на объект модели, к которому добавляется заметка.  
  
-   Чтобы снабдить заметками транзакции всех пользователей, необходимо иметь разрешение на доступ к функциональной области **Управление версиями** и являться администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-annotate-a-transaction-in-explorer"></a>Добавление заметки к транзакции в браузере  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  На панели меню наведите указатель на пункт **Сущности** и выберите сущность, содержащую элемент с транзакцией, к которой необходимо добавить заметку.  
  
5.  На сетке щелкните строку элемента.  
  
6.  Нажмите кнопку **Просмотреть транзакции**.  
  
7.  В диалоговом окне **Просмотр транзакций** выберите транзакцию, к которой необходимо добавить заметку.  
  
8.  Введите заметку в поле в нижней части диалогового окна.  
  
9. Нажмите кнопку **Добавить заметку**. Заметка отображается на панели **Заметки** .  
  
### <a name="to-annotate-a-transaction-in-version-management-administrators-only"></a>Добавление заметки к транзакции в управлении версиями (только администраторы)  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] нажмите **Управление версиями**.  
  
2.  В строке меню выберите пункт **Транзакции**.  
  
3.  На панели **Транзакции** щелкните строку в сетке, соответствующую транзакции, которую необходимо снабдить заметкой.  
  
4.  На панели **Заметки транзакции** в поле **Заметка** введите заметку.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Заметки (службы Master Data Services)](../master-data-services/annotations-master-data-services.md)   
 [Транзакции (службы Master Data Services)](../master-data-services/transactions-master-data-services.md)  
  
  

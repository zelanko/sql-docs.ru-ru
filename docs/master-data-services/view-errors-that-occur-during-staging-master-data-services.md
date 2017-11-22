---
title: "Просмотр ошибок, возникающих во время помещения на промежуточное хранение (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
caps.latest.revision: "8"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5b6ae51592297a748d4a1e39a71bed0b2fc921b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="view-errors-that-occur-during-staging-master-data-services"></a>Просмотр ошибок, возникающих во время помещения на промежуточное хранение (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно просмотреть ошибки, которые возникают в ходе промежуточного процесса. В базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] существуют два представления, в которых показываются ошибки:  
  
-   Stg.viw_name_MemberErrorDetails для обновлений конечных или объединенных элементов.  
  
-   Stg.viw_name_RelationshipErrorDetails для обновления связей иерархии.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   В базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] необходимо иметь разрешения SELECT для представления stg.viw_name_MemberErrorDetails или stg.viw_name_RelationshipErrorDetails.  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-view-staging-errors"></a>Для просмотра промежуточных ошибок  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Откройте новый запрос.  
  
3.  Введите следующий текст, заменяя имя именем своей промежуточной таблицы, например viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Выполните запрос. Сведения об ошибках отображаются в поле **ErrorDescription** .  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о сообщениях об ошибках см. в разделе [Ошибки промежуточного процесса (службы Master Data Services)](../master-data-services/staging-process-errors-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Обзор: импорт данных из таблиц (службы Master Data Services)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Устранение неполадок в промежуточном процессе (службы Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  

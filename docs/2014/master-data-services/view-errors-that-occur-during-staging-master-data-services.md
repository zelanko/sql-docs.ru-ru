---
title: Просмотреть ошибки, возникающие в ходе промежуточного процесса (Master Data Services) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c12a96fc1e842775556cf3b1261d7aab2b7cacab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194506"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a>Возможность просмотра ошибки, которая возникает в ходе промежуточного процесса (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно просмотреть ошибки, которые возникают в ходе промежуточного процесса. В базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] существуют два представления, в которых показываются ошибки:  
  
-   Stg.viw_name_MemberErrorDetails для обновлений конечных или объединенных элементов.  
  
-   Stg.viw_name_RelationshipErrorDetails для обновления связей иерархии.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   В базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] необходимо иметь разрешения SELECT для представления stg.viw_name_MemberErrorDetails или stg.viw_name_RelationshipErrorDetails.  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-view-staging-errors"></a>Для просмотра промежуточных ошибок  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Откройте новый запрос.  
  
3.  Введите следующий текст, заменяя имя именем своей промежуточной таблицы, например viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Выполните запрос. Сведения об ошибках отображаются в поле **ErrorDescription** .  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о сообщениях об ошибках см. в разделе [Ошибки промежуточного процесса (службы Master Data Services)](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [Импорт данных &#40;службы Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Устранение неполадок в промежуточном процессе (службы Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
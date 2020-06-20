---
title: Просмотр ошибок, происходящих во время промежуточного процесса (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 10ec88695b4df1e2d4ee5ec7f446574961adc76b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970934"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a>Возможность просмотра ошибки, которая возникает в ходе промежуточного процесса (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно просмотреть ошибки, которые возникают в ходе промежуточного процесса. В базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] существуют два представления, в которых показываются ошибки:  
  
-   Stg.viw_name_MemberErrorDetails для обновлений конечных или объединенных элементов.  
  
-   Stg.viw_name_RelationshipErrorDetails для обновления связей иерархии.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   В базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] необходимо иметь разрешения SELECT для представления stg.viw_name_MemberErrorDetails или stg.viw_name_RelationshipErrorDetails.  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-view-staging-errors"></a>Для просмотра промежуточных ошибок  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Откройте новый запрос.  
  
3.  Введите следующий текст, заменяя имя именем своей промежуточной таблицы, например viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Выполните запрос. Сведения об ошибках отображаются в поле **ErrorDescription** .  
  
## <a name="next-steps"></a>Next Steps  
 Дополнительные сведения о сообщениях об ошибках см. в разделе [Ошибки промежуточного процесса (службы Master Data Services)](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Master Data Services &#40;импорта данных&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Устранение неполадок в промежуточном процессе (службы Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  

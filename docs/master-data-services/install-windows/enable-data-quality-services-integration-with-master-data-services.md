---
title: "Включение интеграции служб Data Quality Services со службами Master Data Services | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
caps.latest.revision: 5
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 50488f539ba00055f4b515a41dca47594c5d3f0d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>Включение интеграции служб Data Quality Services со службами Master Data Services
  В службах [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]соответствующие функциональные возможности обеспечиваются службами Data Quality Services. Для того чтобы использовать эти функции, их следует активировать.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Веб-приложение и база данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] должны существовать.  
  
-   Компонент служб Data Quality Services и клиент DQS должны быть установлены на том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором размещена база данных служб MDS. Дополнительные сведения см. в разделе [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
### <a name="to-enable-data-quality-services-integration"></a>Включение интеграции служб Data Quality Services  
  
1.  Откройте среду [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
3.  На странице **Веб-конфигурация** выберите веб-сайт и веб-приложение.  
  
4.  В разделе **Включение интеграции DQS** выберите пункт **Включить интеграцию со службами Data Quality Services**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление качества данных в надстройке MDS для Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Надстройка Master Data Services для Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  

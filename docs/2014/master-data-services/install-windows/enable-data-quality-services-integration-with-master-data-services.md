---
title: Включение интеграции служб Data Quality Services со службами Master Data Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 28dc70c0bb2edaa54109c0ea1fc6485c1b00ab52
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212744"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>Включение интеграции служб Data Quality Services со службами Master Data Services
  В службах [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]соответствующие функциональные возможности обеспечиваются службами Data Quality Services. Для того чтобы использовать эти функции, их следует активировать.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Веб-приложение и база данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] должны существовать.  
  
-   Компонент служб Data Quality Services и клиент DQS должны быть установлены на том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором размещена база данных служб MDS. Дополнительные сведения см. в разделе [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
### <a name="to-enable-data-quality-services-integration"></a>Включение интеграции служб Data Quality Services  
  
1.  Откройте среду [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
3.  На странице **Веб-конфигурация** выберите веб-сайт и веб-приложение.  
  
4.  В разделе **Включение интеграции DQS** выберите пункт **Включить интеграцию со службами Data Quality Services**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Сопоставление качества данных в надстройка MDS для Excel](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Надстройка Master Data Services для Microsoft Excel](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [Установка служб Master Data Services](install-master-data-services.md)  
  
  

---
title: Места обработки и хранения (мастер секционирования) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifyprocessingandstorage.f1
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eae2e7c380b7b0de69047079edac87d273f07d52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286060"
---
# <a name="processing-and-storage-locations-partition-wizard"></a>Места обработки и хранения (мастер секционирования)
  На странице **Места обработки и хранения** можно определить экземпляр служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] куба, владеющий секцией, а также экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , где хранятся данные секции. Чтобы определить секцию как удаленную, укажите либо удаленный экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , либо место хранения, отличающееся от места хранения по умолчанию. Дополнительные сведения об удаленных секциях см. в разделе [Удаленные секции](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).  
  
## <a name="processing-location-options"></a>Параметры места обработки  
 **Текущий экземпляр сервера**  
 Назначает текущий экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ответственным за обработку секции.  
  
 **Удаленный источник данных служб Analysis Services**  
 Назначает удаленный экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ответственным за обработку этой секции.  
  
 Из раскрывающегося списка выберите источник данных, являющийся удаленным экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , который будет отвечать за обработку секции.  
  
> [!NOTE]  
>  Если выбран источник данных, в котором значение свойства строки соединения `Initial Catalog` не соответствует допустимой базе данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], либо если база данных, указанная в свойстве строки соединения `Initial Catalog`, не поддерживает удаленные секции (то есть значение свойства `MasterDatasourceID` для указанной базы данных не является допустимым), возникает ошибка.  
  
 **Создать**  
 Создание нового источника данных, представляющего собой удаленный экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , ответственный за обработку секции.  
  
## <a name="storage-location-options"></a>Параметры места хранения  
 **Размещение сервера по умолчанию**  
 Папка данных текущего экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] становится местом хранения статистических данных и данных индексирования для секции.  
  
 **Указанная папка**  
 Задает место хранения статистических данных и данных индексирования для секции.  
  
 **...**  
 Выводит диалоговое окно **Выбор удаленной папки** , в котором можно выбрать папку для поля **Указанная папка**.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера секционирования &#40;службы Analysis Services — многомерные данные&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md)   
 [Секции &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Выбор удаленной папки-диалоговое окно &#40;службы Analysis Services — многомерные данные&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
  

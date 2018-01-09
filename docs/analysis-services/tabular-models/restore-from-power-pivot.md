---
title: "Восстановление из Power Pivot | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7beb148b2090fcdcb7a150d3b5eb789beaf7bb08
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="restore-from-power-pivot"></a>Восстановление из Power Pivot
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Можно использовать операцию восстановления из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] компонентов в SQL Server Management Studio для создания новой базы данных табличной модели на экземпляре служб Analysis Services (работающем в табличном режиме) или восстановить имеющуюся базу данных из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книги (XLSX).  
  
> [!NOTE]  
>  Команда импорта из шаблона проекта [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в среде SQL Server Data Tools обладает схожими функциями. Дополнительные сведения см. в разделе [Импорт из PowerPivot (табличные службы SSAS)](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md).  
  
 При использовании команды восстановления из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]учитывайте следующее:  
  
-   Чтобы выполнить восстановление из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], следует войти в экземпляр служб Analysis Services в качестве участника роли администратора сервера.  
  
-   Учетная запись экземпляра служб Analysis Services должна иметь разрешения на чтение файла книги, из которой проводится восстановление.  
  
-   По умолчанию при восстановлении базы данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]для свойства табличного шаблона базы данных "Сведения об олицетворении источника данных" задано значение "По умолчанию", что означает применение учетной записи экземпляра служб Analysis Services. Рекомендуется изменить учетные данные олицетворения на учетную запись Windows в свойствах базы данных. Дополнительные сведения см. в разделе [Олицетворение (табличные службы SSAS)](../../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
-   Информация из модели данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] будет скопирована в существующий или новый табличный шаблон базы данных экземпляра служб Analysis Services. Если книга [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] содержит связанные таблицы, они будут воссозданы как таблицы без источника данных аналогично тем, которые создаются командой "Вставить в новую таблицу".  
  
### <a name="to-restore-from-power-pivot"></a>Восстановление из Power Pivot  
  
1.  В среде SSMS в экземпляре Active Directory, в который ведется восстановление, щелкните правой кнопкой мыши **Базы данных**, а затем выберите **Восстановление из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**.  
  
2.  В диалоговом окне **Восстановление из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]** на вкладке **Источник восстановления** в поле **Файл резервной копии** нажмите кнопку **Обзор** и выберите файл с расширением ABF или XSLX, из которого следует производить восстановление.  
  
3.  В поле **Цель восстановления**области **Восстановление базы данных**введите имя новой или существующей базы данных. Если имя не указано, будет использовано имя книги.  
  
4.  В поле **Место хранения**нажмите кнопку **Обзор**и выберите расположение для хранения базы данных.  
  
5.  В области **Параметры**оставьте флажок **Включить сведения о безопасности** . При восстановлении из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] этот параметр не действует.  
  
## <a name="see-also"></a>См. также:  
 [Базы данных табличной модели (табличные службы SSAS)](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)   
 [Импорт из PowerPivot (табличные службы SSAS)](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)  
  
  

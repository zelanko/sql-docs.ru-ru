---
title: Восстановление из Power Pivot в службах Analysis Services | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 75290c6b877c3bb10cd42fbb10f1c087310791d3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472254"
---
# <a name="restore-from-power-pivot"></a>Восстановление из Power Pivot
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Можно использовать операцию восстановления из компонента [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] среды SQL Server Management Studio для создания новой базы данных табличной модели в экземпляре служб Analysis Services (работающем в табличном режиме) или восстановить имеющуюся базу данных из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] (XLSX).  
  
> [!NOTE]  
>  Команда импорта из шаблона проекта [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в среде SQL Server Data Tools обладает схожими функциями. Дополнительные сведения см. в разделе [Импорт из Power Pivot](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md).  
  
 При использовании команды восстановления из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]учитывайте следующее:  
  
-   Чтобы выполнить восстановление из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], следует войти в экземпляр служб Analysis Services в качестве участника роли администратора сервера.  
  
-   Учетная запись экземпляра служб Analysis Services должна иметь разрешения на чтение файла книги, из которой проводится восстановление.  
  
-   По умолчанию при восстановлении базы данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]для свойства табличного шаблона базы данных "Сведения об олицетворении источника данных" задано значение "По умолчанию", что означает применение учетной записи экземпляра служб Analysis Services. Рекомендуется изменить учетные данные олицетворения на учетную запись Windows в свойствах базы данных. Дополнительные сведения см. в разделе [олицетворения](../../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
-   Информация из модели данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] будет скопирована в существующий или новый табличный шаблон базы данных экземпляра служб Analysis Services. Если книга [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] содержит связанные таблицы, они будут воссозданы как таблицы без источника данных аналогично тем, которые создаются командой "Вставить в новую таблицу".  
  
### <a name="to-restore-from-power-pivot"></a>Восстановление из Power Pivot  
  
1.  В среде SSMS в экземпляре Active Directory, в который ведется восстановление, щелкните правой кнопкой мыши **Базы данных**, а затем выберите **Восстановление из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**.  
  
2.  В диалоговом окне **Восстановление из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]** на вкладке **Источник восстановления** в поле **Файл резервной копии** нажмите кнопку **Обзор** и выберите файл с расширением ABF или XSLX, из которого следует производить восстановление.  
  
3.  В поле **Цель восстановления**области **Восстановление базы данных**введите имя новой или существующей базы данных. Если имя не указано, будет использовано имя книги.  
  
4.  В поле **Место хранения**нажмите кнопку **Обзор**и выберите расположение для хранения базы данных.  
  
5.  В области **Параметры**оставьте флажок **Включить сведения о безопасности** . При восстановлении из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] этот параметр не действует.  
  
## <a name="see-also"></a>См. также  
 [Базы данных табличной модели](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)   
 [Импорт из Power Pivot](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)  
  
  

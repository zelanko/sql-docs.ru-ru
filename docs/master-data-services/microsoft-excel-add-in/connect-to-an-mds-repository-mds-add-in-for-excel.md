---
title: "Соединение с репозиторием MDS (надстройка MDS для Excel) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: microsoft-excel-add-in
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
caps.latest.revision: 12
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 29208bf4a5d131e47ded0ba55aa167f6ee80ff3f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a>Соединение с репозиторием MDS (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]необходимо установить соединение с репозиторием MDS, прежде чем можно будет загружать или публиковать данные.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
### <a name="to-connect-to-an-mds-repository"></a>Соединение с репозиторием MDS  
  
1.  В MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]на вкладке **Основные данные** в группе **Соединение и загрузка** нажмите стрелку под кнопкой **Соединение** и выберите команду **Управление соединениями**.  
  
2.  В диалоговом окне **Управление соединениями** в разделе **Новое соединение** нажмите кнопку **Создать новое соединение**.  
  
3.  Нажмите кнопку **Создать**.  
  
4.  В диалоговом окне **Добавление нового соединения** в поле **Описание** введите описание соединения. Это соединение будет отображаться при нажатии стрелки кнопки **Соединение** на панели инструментов.  
  
5.  В поле **Адрес сервера MDS** введите URL-адрес веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], например `http://contoso/mds`.  
  
    > [!NOTE]  
    >  Следует использовать имя компьютера, а не «localhost».  
  
6.  Нажмите кнопку **ОК**. Это имя появится в разделе **Существующие соединения** .  
  
7.  Можно нажать кнопку **Проверка** , чтобы проверить соединение. Будет выдано диалоговое окно подтверждения или сообщение об ошибке. Чтобы закрыть его, нажмите кнопку **ОК** .  
  
8.  Нажмите кнопку **Соединить**. Отображается панель **Службы Master Data Services** .  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Export Data to Excel from Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)  
  
-   [Фильтрация данных перед их экспортом (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Соединения (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
  


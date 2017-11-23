---
title: "Импорт пакета управления SCOM для PDW (система платформы аналитики)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa735041-8e58-4886-ae3b-36f3c6298b12
caps.latest.revision: "6"
ms.openlocfilehash: 2766219fc98a1a3f0174b2c33846fcedb0b74022
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="import-the-scom-management-pack-for-pdw"></a>Импорт пакета управления SCOM для PDW
Выполните следующие действия для импорта пакетов управления System Center Operations Manager (SCOM) для SQL Server PDW. Пакеты управления требуются для наблюдения за SQL Server PDW из SCOM.  
  
## <a name="BeforeBegin"></a>Перед началом  
**Предварительные требования**  
  
System Center Operations Manager 2007 R2 должны быть установлены и запущены.  
  
Пакеты управления должны быть установлены. В разделе [установить пакеты управления SCOM &#40; Система платформы аналитики &#41; ](install-the-scom-management-packs.md).  
  
## <a name="Step1"></a>Шаг 1: Импорт Appliance базовый пакет управления SQL Server  
  
1.  Войдите в систему под учетной записью, которая является членом роли администраторов Operations Manager для группы управления Operations Manager 2007.  
  
2.  В консоли управления щелкните **администрирования**.  
  
3.  Щелкните правой кнопкой мыши **пакетов управления** , а затем щелкните **Импорт пакетов управления**.  
  
    ![Нажмите кнопку Импорт пакетов управления](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM")  
  
4.  В списке пакетов управления, выберите пакет управления, который требуется импортировать, нажмите кнопку **выберите**, а затем нажмите кнопку **добавить**.  
  
    ![Список пакетов управления](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  Поиск **устройство** и затем детализации база устройства SQL Server и нажмите кнопку **добавить** два варианта.  
  
    ![База устройства SQL Server](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  В нижней области выбранного были два пакета управления, щелкните **ОК**.  
  
    ![Выберите оба пакета управления](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  Нажмите кнопку **Установить**.  
  
    ![Нажмите "установить"](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  После завершения нажмите кнопку **закрыть**.  
  
    ![После завершения нажмите кнопку Закрыть](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Импортируйте пакет мониторинга для устройства в хранилище параллельных данных Microsoft SQL Server 2008 R2  
  
1.  Щелкните правой кнопкой мыши **пакетов управления** , а затем щелкните **Импорт пакетов управления**.  
  
2.  Выберите **добавить с диска**...  
  
    ![Щелкните правой кнопкой мыши пакеты управления](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  Перейдите к расположению, в которую было извлечено пакеты управления SQL Server PDW и выберите три пакета управления, которые приведены в разделе «Импорт пакетов управления выбранные». Это можно сделать путем выбора первого из них, нажав клавишу Shift и выбрав последним. Когда все они были выбраны, щелкните **откройте**.  
  
    ![Выберите пакеты управления](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  Нажмите кнопку **Установить**.  
  
    ![Нажмите "установить"](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Щелкните **Закрыть**.  
  
    ![Нажмите кнопку Закрыть](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>Следующий шаг  
Импортированных пакетов управления, перейти к следующему шагу: [настройки SCOM для монитора Analytics Platform System &#40; Система платформы аналитики &#41; ](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  

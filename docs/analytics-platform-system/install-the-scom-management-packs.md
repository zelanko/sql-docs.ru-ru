---
title: "Установить пакеты управления SCOM (система платформы аналитики)"
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
ms.assetid: ab3985d8-0a71-4b28-9d28-9886ae2a110f
caps.latest.revision: "16"
ms.openlocfilehash: f20048a70ef04bba475f9e8e6b58b24095f23f1a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="install-the-scom-management-packs"></a>Установить пакеты управления SCOM
Выполните следующие действия, чтобы загрузить и установить пакеты управления System Center Operations Manager (SCOM) для SQL Server PDW. Пакеты управления требуются для наблюдения за SQL Server PDW из SCOM.  
  
## <a name="BeforeBegin"></a>Перед началом  
**Предварительные требования**  
  
System Center Operations Manager должны быть установлены и запущены. SQL Server PDW 2012 требуется System Center Operations Manager 2007 R2, System Center Operations Manager 2012 или System Center Operations Manager 2012 с пакетом обновления 1.  
  
## <a name="Step1"></a>Шаг 1: Загрузка пакетов управления  
Для рабочей нагрузки APS PDW, загрузите [пакет управления System Center для Microsoft Analytics Platform System](http://go.microsoft.com/fwlink/?LinkId=396857).  
  
Для управления устройством, загрузите [пакет управления SQL Server устройства Base](http://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=11436).  
  
Для более старых версий PDW без APS, загрузите[пакету мониторинга System Center для Microsoft SQL Server 2012 Parallel устройством хранилища данных](http://go.microsoft.com/fwlink/p/?LinkId=282661).  
  
Для HDInsight рабочей нагрузки, загрузите [пакет управления System Center для HDInsight](http://go.microsoft.com/fwlink/?LinkId=390208).  
  
## <a name="Step2"></a>Шаг 2: Установка пакетов управления  
  
### <a name="install-the-sql-server-appliance-base-management-pack"></a>Установка устройства базовый пакет управления SQL Server  
  
1.  Чтобы запустить установку, дважды щелкните загруженный Appliance Base пакет управления SQL Server.  
  
2.  Примите лицензионное соглашение и нажмите кнопку **Далее**.  
  
    ![Примите лицензионное соглашение](./media/install-the-scom-management-packs/SCOM_licnse_agrmt.png "SCOM_licnse_agrmt")  
  
3.  Выберите папку установки, или использовать значение по умолчанию папка установки пакета управления.  
  
    ![Выберите папку установки](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
4.  Нажмите кнопку **Установить**.  
  
    ![Подтверждение установки](./media/install-the-scom-management-packs/SCOM_licnse_agrmt3.png "SCOM_licnse_agrmt3")  
  
5.  Щелкните **Закрыть**.  
  
    ![Нажмите кнопку Закрыть](./media/install-the-scom-management-packs/SCOM_licnse_agrmt4.png "SCOM_licnse_agrmt4")  
  
### <a name="install-the-monitoring-pack-for-sql-server-pdw-appliance"></a>Установка пакета мониторинга для SQL Server PDW Appliance  
  
1.  Чтобы запустить установку, дважды щелкните загруженный PDW Appliance пакет управления SQL Server.  
  
2.  Примите лицензионное соглашение и нажмите кнопку **Далее**.  
  
    ![Примите лицензионное соглашение](./media/install-the-scom-management-packs/SCOM_licnse_agmtB.png "SCOM_licnse_agmtB")  
  
3.  Выберите каталог, в котором будет храниться извлеченные файлы. По умолчанию папкой установки пакета управления отображается по умолчанию. Выберите значение по умолчанию или выберите папку установки.  
  
    ![Выбор папки установки](./media/install-the-scom-management-packs/SCOM_licnse_agmtB1.png "SCOM_licnse_agmtB1")  
  
4.  Нажмите кнопку **Установить**.  
  
    ![Подтверждение установки](./media/install-the-scom-management-packs/SCOM_licnse_agmtB2.png "SCOM_licnse_agmtB2")  
  
5.  Щелкните **Закрыть**.  
  
    ![Завершение установки](./media/install-the-scom-management-packs/SCOM_licnse_agmtB3.png "SCOM_licnse_agmtB3")  
  
## <a name="next-step"></a>Следующий шаг  
У вас есть установленных пакетов управления, перейти к следующему шагу: [импортировать пакет управления SCOM для PDW &#40; Система платформы аналитики &#41; ](import-the-scom-management-pack-for-pdw.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  

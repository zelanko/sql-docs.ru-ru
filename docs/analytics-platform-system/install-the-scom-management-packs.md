---
title: Установить пакеты управления SCOM - система платформы аналитики | Документы Microsoft
description: Выполните следующие действия, чтобы загрузить и установить пакеты управления System Center Operations Manager (SCOM) для SQL Server PDW. Пакеты управления требуются для наблюдения за SQL Server PDW из SCOM.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 163ab893074e171decb573d876c5f98334437985
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="install-sql-server-operations-manager-scom-management-packs-for-analytics-platform-system"></a>Установить пакеты управления SQL Server Operations Manager (SCOM) для система платформы аналитики
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
У вас есть установленных пакетов управления, перейти к следующему шагу: [импорта пакета управления SCOM для PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  

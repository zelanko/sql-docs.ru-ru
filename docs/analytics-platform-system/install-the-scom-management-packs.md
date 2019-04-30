---
title: Установить пакеты управления SCOM - Analytics Platform System | Документация Майкрософт
description: Выполните следующие действия, чтобы скачать и установить пакеты управления System Center Operations Manager (SCOM) для SQL Server PDW. Пакеты управления требуются для наблюдения за SQL Server PDW из SCOM.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f0acfa636a3432dcffb18cfec57ee7625c1eb01b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63215523"
---
# <a name="install-sql-server-operations-manager-scom-management-packs-for-analytics-platform-system"></a>Установить пакеты управления SQL Server Operations Manager (SCOM) для системы платформы аналитики
Выполните следующие действия, чтобы скачать и установить пакеты управления System Center Operations Manager (SCOM) для SQL Server PDW. Пакеты управления требуются для наблюдения за SQL Server PDW из SCOM.  
  
## <a name="BeforeBegin"></a>Перед началом  
**Предварительные требования**  
  
System Center Operations Manager должны быть установлены и запущены. SQL Server PDW 2012 требуется System Center Operations Manager 2007 R2, System Center Operations Manager 2012 или System Center Operations Manager 2012 с пакетом обновления 1.  
  
## <a name="Step1"></a>Шаг 1. Загрузить пакеты управления  
Для рабочей нагрузки APS PDW, загрузите [пакет управления System Center для Microsoft Analytics Platform System](https://go.microsoft.com/fwlink/?LinkId=396857).  
  
Для управления устройством, загрузите [пакет управления SQL Server Appliance Base](https://www.microsoft.com/download/details.aspx?displaylang=en&id=11436).  
  
Для более старых версиях PDW без APS, загрузите[пакет мониторинга System Center для Microsoft SQL Server 2012 Parallel виртуальным устройством хранилища данных](https://go.microsoft.com/fwlink/p/?LinkId=282661).  
  
<!-- MISSING LINKS - For the HDInsight workload, download the [System Center Management Pack for HDInsight](https://go.microsoft.com/fwlink/?LinkId=390208).  -->
  
## <a name="Step2"></a>Шаг 2. Установить пакеты управления  
  
### <a name="install-the-sql-server-appliance-base-management-pack"></a>Установить SQL Server Appliance базовый пакет управления  
  
1.  Чтобы выполнить установку, дважды щелкните загруженный модуль базовый пакет управления SQL Server.  
  
2.  Примите лицензионное соглашение и нажмите кнопку **Далее**.  
  
    ![Примите лицензионное соглашение](./media/install-the-scom-management-packs/SCOM_licnse_agrmt.png "SCOM_licnse_agrmt")  
  
3.  Выберите папку установки, или используйте значение по умолчанию папка установки пакета управления.  
  
    ![Выберите папку установки](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
4.  Нажмите кнопку **Установить**.  
  
    ![Подтверждение установки](./media/install-the-scom-management-packs/SCOM_licnse_agrmt3.png "SCOM_licnse_agrmt3")  
  
5.  Щелкните **Закрыть**.  
  
    ![Нажмите кнопку Закрыть](./media/install-the-scom-management-packs/SCOM_licnse_agrmt4.png "SCOM_licnse_agrmt4")  
  
### <a name="install-the-monitoring-pack-for-sql-server-pdw-appliance"></a>Установить пакет мониторинга для SQL Server PDW Appliance  
  
1.  Чтобы выполнить установку, дважды щелкните Скачанный SQL Server PDW Appliance пакете управления.  
  
2.  Примите лицензионное соглашение и нажмите кнопку **Далее**.  
  
    ![Примите лицензионное соглашение](./media/install-the-scom-management-packs/SCOM_licnse_agmtB.png "SCOM_licnse_agmtB")  
  
3.  Выберите каталог, который будет содержать извлеченные файлы. По умолчанию папкой установки пакет управления отображается по умолчанию. Выберите параметр по умолчанию, или выберите папку установки.  
  
    ![Выбор папки установки](./media/install-the-scom-management-packs/SCOM_licnse_agmtB1.png "SCOM_licnse_agmtB1")  
  
4.  Нажмите кнопку **Установить**.  
  
    ![Подтверждение установки](./media/install-the-scom-management-packs/SCOM_licnse_agmtB2.png "SCOM_licnse_agmtB2")  
  
5.  Щелкните **Закрыть**.  
  
    ![Завершение установки](./media/install-the-scom-management-packs/SCOM_licnse_agmtB3.png "SCOM_licnse_agmtB3")  
  
## <a name="next-step"></a>Следующий шаг  
Теперь, когда у вас есть установленные пакеты управления, перейдите к следующему шагу: [Импорт пакета управления SCOM для PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  

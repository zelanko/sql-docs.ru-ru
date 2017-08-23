---
title: "Microsoft Connectors for Oracle and Teradata компании attunity (службы SSIS) | Документы Microsoft"
ms.date: 05/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 926c0c51b5a55a2869b73666f5620fa56e139cca
ms.openlocfilehash: fd8b0177227167f6caa3417029bb2acb974fe181
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="microsoft-connectors-for-oracle-and-teradata-by-attunity-for-integration-services-ssis"></a>Microsoft Connectors for Oracle and Teradata by Attunity для служб Integration Services (SSIS)

Вы можете загрузить соединители для служб Integration Services от Attunity, оптимизации производительности при загрузке данных из Oracle или Teradata и в пакете служб SSIS.

## <a name="download-the-latest-attunity-connectors"></a>Скачать последнюю соединители компании Attunity

Получение последней версии соединителей здесь:  
[Соединители Microsoft версии 5.0 для Oracle и Teradata](https://www.microsoft.com/download/details.aspx?id=55179)

## <a name="issue---the-attunity-connectors-arent-visible-in-the-ssis-toolbox"></a>Проблема — Attunity соединителей не отображаются в области элементов служб SSIS

Для просмотра Attunity соединителей в область элементов служб SSIS, всегда следует установить версию соединителей, что целевые объекты совпадает с версией сервера SQL Server версии из SQL Server Data Tools (SSDT) установлены на компьютере. (Также может иметь более ранних версий соединителей.) Это требование не зависит от версии SQL Server, вы будете работать в проекты служб SSIS и пакетов.

Например при установке последней версии SSDT установлена версия 17 SSDT номером сборки, которая начинается с 14. Эта версия SSDT добавляет поддержку 2017 г. SQL Server. Чтобы видеть и использовать Attunity соединители служб SSIS пакет разработки — даже в том случае, если требуется более раннюю версию SQL Server — также необходимо установить последнюю версию соединителей Attunity версии 5.0. Эта версия соединителей также добавлена поддержка 2017 г. SQL Server.

Проверьте установленную версию SSDT для Visual Studio из **справки** | **о Microsoft Visual Studio**, или в **программы и компоненты** на панели управления. Затем установите соответствующую версию соединители Attunity из следующей таблицы.

|Версия SSDT|Номер сборки SSDT|Целевая версия SQL Server|Требуемая версия соединителей|
|---------|---------|---------|---------|
|17|Начинается с 14|SQL Server 2017|[Соединители Microsoft версии 5.0 для Oracle и Teradata](https://www.microsoft.com/download/details.aspx?id=55179)|
|16|Начинается с 13|SQL Server 2016|[Соединители Microsoft версии 4.0 для Oracle и Teradata](https://www.microsoft.com/download/details.aspx?id=52950)|
||||

## <a name="download-the-latest-sql-server-data-tools-ssdt"></a>Загрузить последние данные Tools (SSDT) SQL Server

Получите последнюю версию SSDT здесь:  
[Скачать SQL Server Data Tools (SSDT)](..//ssdt/download-sql-server-data-tools-ssdt.md)

---
title: Соединители Microsoft для Oracle и Teradata компании Attunity | Документация Майкрософт
ms.date: 08/16/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ''
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bcf543438e3d1490f74df7a92a12545f29eeb5f2
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "77903836"
---
# <a name="microsoft-connectors-for-oracle-and-teradata-by-attunity-for-integration-services-ssis"></a>Соединители Microsoft для Oracle и Teradata компании Attunity для служб Integration Services (SSIS)

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

> [!NOTE]
> Соединители Atunity для Oracle и Teradata поддерживают SQL Server 2017 и более ранних версий.
>
> Последние соединители для Oracle и Teradata для SQL Server 2019 и последующих версий можно получить здесь:
> - [Соединитель с Oracle (Microsoft)](data-flow/oracle-connector.md)
> - [Соединитель с Teradata (Microsoft)](data-flow/teradata-connector.md)

Вы можете скачать соединители для служб Integration Services от Attunity, позволяющие оптимизировать производительность при загрузке данных из Oracle или Teradata и в эти системы в пакете служб SSIS.

## <a name="download-the-latest-attunity-connectors"></a>Скачать последние версии соединителей компании Attunity

Получить последнюю версию соединителей:  
[Соединители Microsoft версии 5.0 для Oracle и Teradata](https://www.microsoft.com/download/details.aspx?id=55179)

## <a name="issue---the-attunity-connectors-arent-visible-in-the-ssis-toolbox"></a>Проблема. Соединители Attunity не отображаются в панели элементов служб SSIS

Чтобы видеть соединители Attunity в панели элементов служб SSIS, необходимо всегда устанавливать версии соединителей, разработанные для той же версии SQL Server, что и версия SQL Server Data Tools (SSDT), установленная на вашем компьютере. (Также могут быть установлены более ранние версии соединителей.) Это требование не связано с версией SQL Server, на которую ориентированы ваши пакеты и проекты SSIS.

Например, если вы установили последнюю версию SSDT, у вас будет версия SSDT 17, номер сборки которой начинается с 14. В этой версии SSDT добавлена поддержка SQL Server 2017. Чтобы видеть и использовать соединители в пакете служб SSIS, даже если разработка осуществлялась для более ранней версии SQL Server, необходимо установить последнюю версию соединителей Attunity (5.0). В этой версии соединителей также добавлена поддержка SQL Server 2017.

Проверить установленную версию SSDT можно в Visual Studio в меню **Справка** | **О Microsoft Visual Studio** или в разделе **Программы и компоненты** панели управления. После этого установите соответствующую версию соединителей Attunity, руководствуясь следующей таблицей.

|Версия SSDT|Номер сборки SSDT|Целевая версия SQL Server|Требуемая версия соединителей|
|---------|---------|---------|---------|
|17|Начинается с 14|SQL Server 2017|[Соединители Microsoft версии 5.0 для Oracle и Teradata](https://www.microsoft.com/download/details.aspx?id=55179)|
|16|Начинается с 13|SQL Server 2016|[Соединители Microsoft версии 4.0 для Oracle и Teradata](https://www.microsoft.com/download/details.aspx?id=52950)|
||||

## <a name="download-the-latest-sql-server-data-tools-ssdt"></a>Скачать последнюю версию SQL Server Data Tools (SSDT)

Получить последнюю версию SSDT:  
[Скачать SQL Server Data Tools (SSDT)](..//ssdt/download-sql-server-data-tools-ssdt.md)

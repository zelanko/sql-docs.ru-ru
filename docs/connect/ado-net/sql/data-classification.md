---
title: Обнаружение и классификация данных в SqlClient
description: Сведения о том, как проверить, поддерживает ли база данных SQL Server классификацию данных, и о том, как получить доступ к сведениям о классификации данных с помощью объекта SqlDataReader.
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: 6d82bfd3c49576a35b24f5a04cdc2c03dceeb766
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2020
ms.locfileid: "92081503"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>Обнаружение и классификация данных в SqlClient

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Набор функций [обнаружения и классификации данных SQL](../../../relational-databases/security/sql-data-discovery-and-classification.md) служит для обнаружения конфиденциальных данных в базах данных, их классификации, назначения им меток и создания отчетов. SqlClient включает API, предоставляющий сведения об обнаружении и классификации данных только для чтения, если базовый источник поддерживает эту функцию. Доступ к этим сведениям осуществляется через SqlDataReader.

В этом примере приложения показано, как получить доступ к свойствам классификации данных SqlDataReader.

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**См. также:**  

 [Функции SQL Server и ADO.NET](sql-server-features-adonet.md)
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
ms.openlocfilehash: b53e71c4c302145af14c1f2e37f30fe0e3c8f8e2
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725725"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>Обнаружение и классификация данных в SqlClient

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Набор функций [обнаружения и классификации данных SQL](../../../relational-databases/security/sql-data-discovery-and-classification.md?view=sql-server-2017) служит для обнаружения конфиденциальных данных в базах данных, их классификации, назначения им меток и создания отчетов. SqlClient включает API, предоставляющий сведения об обнаружении и классификации данных только для чтения, если базовый источник поддерживает эту функцию. Доступ к этим сведениям осуществляется через SqlDataReader.

В этом примере приложения показано, как получить доступ к свойствам классификации данных SqlDataReader.

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**См. также:**  

 [Функции SQL Server и ADO.NET](sql-server-features-adonet.md)
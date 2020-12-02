---
title: Организация пулов соединений
description: Сведения о объединении подключений в пул, которое представляет собой технику оптимизации, используемую ADO.NET для максимально экономичного открытия подключений к источникам данных.
ms.date: 11/13/2020
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 41842a2eb754aedc31bad206ad427a86bb65f00f
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96126510"
---
# <a name="connection-pooling"></a>Организация пулов соединений

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

На соединение с источником данных может требоваться значительное время. Чтобы свести к минимуму затраты на открытие подключений, в ADO.NET используется техника *объединения подключений в пул*, которая позволяет минимизировать затраты на часто открываемые и закрываемые подключения.

## <a name="in-this-section"></a>в этом разделе  

[Объединение подключений в пул в SQL Server (ADO.NET)](sql-server-connection-pooling.md) Общие сведения об объединении подключений в пул и описание принципов такого объединения в SQL Server.

## <a name="see-also"></a>См. также

- [Извлечение и изменение данных в ADO.NET](retrieving-modifying-data.md)

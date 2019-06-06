---
title: Поставщики данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 30d1e1515ed3e84640fe1ca004cb7cbf4383ce97
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718717"
---
# <a name="data-providers"></a>Поставщики данных
Поставщики данных представляют различных источников данных, таких как базы данных SQL, индексированных последовательных файлов, электронных таблиц, хранилищ документов и почтовых файлов. Поставщики предоставляют данные равномерно через общие абстракция, которая называется набор строк.  
  
 ADO — мощная и гибкая, так как он может подключиться к любому из нескольких разных поставщиков данных и по-прежнему предоставлять ту же модель программирования, независимо от конкретных функциях любого данного поставщика. Тем не менее так как каждый поставщик данных является уникальным, как приложение взаимодействует с ADO зависит от поставщика данных.  
  
 Например возможности и компоненты поставщика OLE DB для SQL Server, который используется для доступа к базам данных Microsoft SQL Server, значительно отличаются от тех, которые поставщика Microsoft OLE DB для публикаций в Интернете, который используется для доступа к файлу хранилищ на веб-сервере.

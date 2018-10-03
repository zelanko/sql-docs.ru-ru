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
manager: craigg
ms.openlocfilehash: 3c3b8a4ac0da80303a63bd62f7b4d6f51faab1fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692942"
---
# <a name="data-providers"></a>Поставщики данных
Поставщики данных представляют различных источников данных, таких как базы данных SQL, индексированных последовательных файлов, электронных таблиц, хранилищ документов и почтовых файлов. Поставщики предоставляют данные равномерно через общие абстракция, которая называется набор строк.  
  
 ADO — мощная и гибкая, так как он может подключиться к любому из нескольких разных поставщиков данных и по-прежнему предоставлять ту же модель программирования, независимо от конкретных функциях любого данного поставщика. Тем не менее так как каждый поставщик данных является уникальным, как приложение взаимодействует с ADO зависит от поставщика данных.  
  
 Например возможности и компоненты поставщика OLE DB для SQL Server, который используется для доступа к базам данных Microsoft SQL Server, значительно отличаются от тех, которые поставщика Microsoft OLE DB для публикаций в Интернете, который используется для доступа к файлу хранилищ на веб-сервере.

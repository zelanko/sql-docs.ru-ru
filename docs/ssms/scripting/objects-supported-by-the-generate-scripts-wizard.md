---
title: Объекты, поддерживаемые мастером создания скриптов
description: Ознакомьтесь с типами объектов, которые можно публиковать с помощью мастера формирования и публикации скриптов.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: ssms
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c9715b44bdd664378842bad70ed4f0d0fea913ab
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88901837"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Объекты, поддерживаемые мастером создания скриптов
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Мастер создания и публикации скриптов поддерживает подмножество объектов, поддерживаемое компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Поддерживаемые объекты  
 В следующей таблице перечислены объекты, которые можно публиковать при поддержке мастера формирования и публикации скриптов.  
  
:::row:::
    :::column:::
        Роль приложения
    :::column-end:::
    :::column:::
        роль базы данных;
    :::column-end:::
    :::column:::
        схема
    :::column-end:::
    :::column:::
        Определяемое пользователем статистическое выражение
    :::column-end:::
    :::column:::
        Представление*
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Сборка
    :::column-end:::
    :::column:::
        Ограничение DEFAULT
    :::column-end:::
    :::column:::
        Хранимая процедура*
    :::column-end:::
    :::column:::
        Определяемый пользователем тип данных
    :::column-end:::
    :::column:::
        Коллекция схем XML
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Ограничение CHECK
    :::column-end:::
    :::column:::
        Полнотекстовый каталог
    :::column-end:::
    :::column:::
        Синоним
    :::column-end:::
    :::column:::
        Определяемая пользователем функция
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Хранимая процедура среды CLR*
    :::column-end:::
    :::column:::
        Индекс
    :::column-end:::
    :::column:::
        Таблица
    :::column-end:::
    :::column:::
        Определяемая пользователем таблица
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Определяемая пользователем функция CLR
    :::column-end:::
    :::column:::
        Правило
    :::column-end:::
    :::column:::
        Пользователь**
    :::column-end:::
    :::column:::
        Определяемый пользователем тип
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

 *Опубликовано без шифрования.  
  
 **Все несистемные пользователи, существующие в базе данных, будут опубликованы как роли.  
  
  

---
title: Объекты, поддерживаемые мастером создания скриптов
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c14ea09d45c59def95f078eb87e72e2a70925892
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253760"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Объекты, поддерживаемые мастером создания скриптов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Мастер создания и публикации скриптов поддерживает подмножество объектов, поддерживаемое компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Поддерживаемые объекты  
 В следующей таблице перечислены объекты, которые можно публиковать при поддержке мастера формирования и публикации скриптов.  
  
||||||  
|-|-|-|-|-|  
|Роль приложения|роль базы данных;|схема|Определяемое пользователем статистическое выражение|Представление*|  
|Сборка|Ограничение DEFAULT|Хранимая процедура*|Определяемый пользователем тип данных|Коллекция схем XML|  
|Ограничение CHECK|Полнотекстовый каталог|Синоним|Определяемая пользователем функция||  
|Хранимая процедура среды CLR*|Индекс|Таблица|Определяемая пользователем таблица||  
|Определяемая пользователем функция CLR|Правило|Пользователь**|Определяемый пользователем тип||  
  
 *Опубликовано без шифрования.  
  
 **Все несистемные пользователи, существующие в базе данных, будут опубликованы как роли.  
  
  

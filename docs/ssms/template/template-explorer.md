---
description: Template Explorer
title: Template Explorer
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.templates.explorer.f1
- sql13.wb.templates.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 5fcf7040cbf7b0dc3982164ca6574f2c048ed28c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468530"
---
# <a name="template-explorer"></a>Template Explorer

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет целый ряд шаблонов. Шаблоны — это файлы со стандартным текстом, содержащие скрипты SQL, которые помогают создавать объекты в базе данных. После первого открытия обозревателя шаблонов копия шаблонов помещается в папку пользователя "AppData\Roaming\Microsoft\SQL Server Management Studio\130\Templates" в "C:\Users".  
  
Предусмотрена возможность просматривать доступные шаблоны в обозревателе шаблонов, затем открывать шаблон для включения его кода в окно редактора кода. Можно также создавать пользовательские шаблоны.  
  
## <a name="benefits-of-templates"></a>Преимущества шаблонов  
Шаблоны доступны для решений, проектов и различных типов редакторов кода. Имеются шаблоны создания таких объектов, как базы данных, таблицы, представления, индексы, хранимые процедуры, триггеры, статистические данные и функции. Кроме того, есть такие шаблоны, которые помогают управлять сервером путем создания расширенных свойств, связанных серверов, имен входа, ролей, пользователей и шаблонов для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)].  
  
Шаблоны, поставляемые со среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , содержат параметры для облегчения настройки кода. После открытия шаблона используйте диалоговое окно **Замена параметров шаблона** для вставки значений в скрипт.  
  
Для часто выполняемых задач можно создать пользовательские шаблоны. Организуйте свои скрипты в существующих папках или создайте новую структуру файлов.  
  
Кроме того, редактор запросов компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)] позволяет вставить фрагменты кода в скрипт, для чего достаточно щелкнуть правой кнопкой мыши в нужном месте скрипта.  
  
## <a name="related-tasks"></a>Связанные задачи  
Используйте следующие разделы, чтобы приступить к работе с шаблонами  
  
|**Описание**|**Раздел**|  
|-------------------|-------------|  
|Описано, как включить код из шаблона в окно редактора кода.|[Открытие шаблона](../../ssms/template/open-a-template.md)|  
|Описано, как заменить значения параметров шаблона после открытия шаблона в редакторе кода.|[Замена параметров шаблона](../../ssms/template/replace-template-parameters.md)|  
  

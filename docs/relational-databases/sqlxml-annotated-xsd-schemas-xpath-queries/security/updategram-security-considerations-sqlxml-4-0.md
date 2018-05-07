---
title: Вопросы безопасности диаграмм обновления (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6f9a1227be077396e9e7575780be16c7b0a9fa04
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updategram-security-considerations-sqlxml-40"></a>Вопросы безопасности диаграмм обновления (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ниже приведены рекомендации по безопасному использованию диаграмм обновления.  
  
-   Рекомендуется избегать использования сопоставления по умолчанию при использовании диаграмм обновления для обновления данных. При использовании сопоставления по умолчанию имя элемента в диаграмме обновления сопоставляется с именем таблицы, а имя атрибута сопоставляется со столбцом. Это представляет собой информацию о таблице базы данных и столбце в базе данных, что может быть потенциальной угрозой безопасности. Вместо этого при указании отдельной схемы сопоставления, которая сопоставляет элементы и атрибуты в диаграмме обновления с таблицами и столбцами базы данных, имена элементов и атрибутов диаграммы обновления могут иметь произвольную форму, а схема делает необходимое сопоставление этих имен с таблицами и столбцами базы данных. Таким образом сведения из базы данных не представлены в диаграмме обновления.  
  
-   Не следует разрешать пользователям создавать и исполнять собственные диаграммы обновления. Рекомендуется сохранять диаграммы обновления в виде шаблонов на сервере, а не создавать их динамически в приложениях ASP-типа, которые создают риск, имея возможность изменять данные в базе данных. Можно избежать этого риска, если предоставить пользователям доступ к данным только через диаграммы обновления, представленные в виде шаблонов.  
  
## <a name="see-also"></a>См. также:  
 [Изменение данных в SQLXML 4.0 с помощью диаграммы обновления](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  

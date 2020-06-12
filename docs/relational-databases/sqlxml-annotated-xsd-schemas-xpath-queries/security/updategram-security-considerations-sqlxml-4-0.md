---
title: Вопросы безопасности диаграмма обновления (SQLXML)
description: Ознакомьтесь с рекомендациями по безопасности для использования диаграмм обновления в SQLXML 4,0.
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 82248c14e91e06249bbde71e9f10918db31be25c
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529862"
---
# <a name="updategram-security-considerations-sqlxml-40"></a>Вопросы безопасности диаграмм обновления (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ниже приведены рекомендации по безопасному использованию диаграмм обновления.  
  
-   Рекомендуется избегать использования сопоставления по умолчанию при использовании диаграмм обновления для обновления данных. При использовании сопоставления по умолчанию имя элемента в диаграмме обновления сопоставляется с именем таблицы, а имя атрибута сопоставляется со столбцом. Это представляет собой информацию о таблице базы данных и столбце в базе данных, что может быть потенциальной угрозой безопасности. Вместо этого при указании отдельной схемы сопоставления, которая сопоставляет элементы и атрибуты в диаграмме обновления с таблицами и столбцами базы данных, имена элементов и атрибутов диаграммы обновления могут иметь произвольную форму, а схема делает необходимое сопоставление этих имен с таблицами и столбцами базы данных. Таким образом сведения из базы данных не представлены в диаграмме обновления.  
  
-   Не следует разрешать пользователям создавать и исполнять собственные диаграммы обновления. Рекомендуется сохранять диаграммы обновления в виде шаблонов на сервере, а не создавать их динамически в приложениях ASP-типа, которые создают риск, имея возможность изменять данные в базе данных. Можно избежать этого риска, если предоставить пользователям доступ к данным только через диаграммы обновления, представленные в виде шаблонов.  
  
## <a name="see-also"></a>См. также:  
 [Использование диаграмм обновления для изменения данных в SQLXML 4.0](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  

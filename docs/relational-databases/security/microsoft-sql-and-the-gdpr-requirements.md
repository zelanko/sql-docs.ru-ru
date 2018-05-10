---
title: Microsoft SQL и требования GDPR | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e5144b4ec829f57b77ae92fb3d55a724bb08964b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="guide-to-enhancing-privacy-and-addressing-gdpr-requirements-with-the-microsoft-sql-platform"></a>Руководство по улучшению конфиденциальности и удовлетворению требований GDPR с помощью платформы Microsoft SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

## <a name="summary"></a>Сводка
25 мая 2018 года вступит в силу европейский закон о конфиденциальности, устанавливающий новый международный стандарт определения, защиты и соблюдения прав на неприкосновенность частной жизни. Генеральный регламент о защите персональных данных (General Data Protection Regulation, GDPR) направлен, прежде всего, на защиту и обеспечение неприкосновенности частной жизни физических лиц и устанавливает строгие международные требования, регулирующие обработку и защиту персональных данных при уважении личного выбора каждого человека. 

Клиентам Microsoft SQL, подпадающим под действие GDPR (управляющим облачными и (или) локальными базами данных), необходимо будет удостовериться, что соответствующие данные в их системах баз данных обрабатываются в надлежащем порядке и защищаются в соответствии с принципами GDRP. Это означает, что многим клиентам придется пересмотреть или изменить процедуры управления базами данных или обработки данных, особенно в том, что касается их защиты в соответствии с GDPR.

Технологии Microsoft SQL предоставляют множество встроенных средств безопасности, способных помочь снизить риски для данных, укрепить их защиту и улучшить управление данными на уровне баз данных и выше. В данном документе рассматриваются эти средства и обсуждаются собственные подходы корпорации Майкрософт к достижению целей по защите конфиденциальности данных, определяемых в GDPR.
   
  
**Автор:** Ронит Реджер (Ronit Reger)

**Технические редакторы:** Конор Каннингем (Conor Cunningham), 	Джоаким Хаммер (Joachim Hammer), Шай Карив (Shai Kariv), Джули Коэсмарно (Julie Koesmarno), Элис Купчик (Alice Kupcik), Рон Матчоро (Ron Matchoro), Джайлад Меттелмен (Gilad Mittelman), Дэн Рэдиске (Dan Rediske) и Томер Вайсберг (Tomer Weisberg) 
  
**Дата публикации:** май 2017 г.  
  
**Область применения:** SQL Server (все версии), База данных SQL Azure, Хранилище данных SQL Azure, Система платформ аналитики 
  
Чтобы ознакомиться с документом, загрузите [Руководство по улучшению конфиденциальности и удовлетворению требований GDPR с помощью платформы Microsoft SQL](http://download.microsoft.com/download/4/9/4/4948194B-A613-49ED-90A5-5144313549AB/microsoft-sql-and-the-gdpr.pdf).   

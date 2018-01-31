---
title: "Выбор таблицы измерения и ключей (мастер медленно изменяющихся измерений) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ffb70a31cf4bf373df74c35912ef05076ae06a18
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Выбрать таблицу измерения и ключи (мастер медленно изменяющихся измерений)
  Страница **Выбор таблицы измерения и ключей** позволяет выбрать для загрузки таблицу измерения. Сопоставьте столбцы из потока с данными столбцов, которые нужно загрузить.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Connection manager**  
 Выберите из списка существующий диспетчер соединений OLE DB или нажмите кнопку **Создать** , чтобы создать диспетчер соединений OLE DB.  
  
> [!NOTE]  
>  Мастер медленно изменяющихся измерений поддерживает только диспетчеры соединений OLE DB и подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Создать**  
 В диалоговом окне **Настройка диспетчера соединений OLE DB** выберите существующий диспетчер соединений или щелкните **Создать** для создания нового соединения OLE DB.  
  
 **Таблица или представление**  
 Выберите таблицу или представление из списка.  
  
 **Входные столбцы**  
 Выберите из списка входные столбцы, для которых можно указать сопоставление.  
  
 **Столбцы измерений**  
 Просмотр всех доступных столбцов измерений.  
  
 **Тип ключа**  
 Выберите один из столбцов измерений в качестве бизнес-ключа. Необходимо иметь один бизнес-ключ.  
  
## <a name="see-also"></a>См. также:  
 [Настройка выходов при помощи мастера медленно изменяющихся измерений](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  

---
title: Выбор таблицы измерения и ключей (мастер медленно изменяющихся измерений) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f93d60b28488dbb910dcb727015c25848db220e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770450"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Выбрать таблицу измерения и ключи (мастер медленно изменяющихся измерений)
  Страница **Выбор таблицы измерения и ключей** позволяет выбрать для загрузки таблицу измерения. Сопоставьте столбцы из потока с данными столбцов, которые нужно загрузить.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Настройка выходов при помощи мастера медленно изменяющихся измерений](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  

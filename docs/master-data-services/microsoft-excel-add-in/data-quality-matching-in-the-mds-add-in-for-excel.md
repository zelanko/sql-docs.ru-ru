---
title: Сопоставление качества данных в надстройке MDS для Excel | Документы Майкрософт
ms.custom: microsoft-excel-add-in
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: be78d051-0d56-46d3-bb89-327e218dadd6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 76f25db84d074a9aeb544daf2fe33b512836daf7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713102"
---
# <a name="data-quality-matching-in-the-mds-add-in-for-excel"></a>Сопоставление качества данных в надстройке MDS для Excel

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Со временем в репозиторий MDS потребуется добавить дополнительные данные. Перед добавлением может быть полезно сравнить новые данные с данными, которые уже управляются в MDS, чтобы избежать дублирования или добавления неточных данных.  
  
 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] использует службы Data Quality Services (DQS) из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для сопоставления данных. При использовании функции сопоставления в надстройке одинаковые записи группируются вместе и выводится показатель, отражающий точность результата. Дополнительные сведения о возможностях сопоставления в службах DQS см. в разделе [Data Matching](../../data-quality-services/data-matching.md).  
  
## <a name="workflow-for-data-quality-matching"></a>Рабочий процесс для сопоставления качества данных  
 При использовании служб DQS с MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]используйте следующий рабочий процесс.  
  
1.  Получите список данных, управляемых MDS, и объедините его со списком данных, которые не управляются в MDS. Дополнительные сведения см. в разделе [Объединение данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md).  
  
2.  Используйте базу набора знаний служб DQS для сравнения данных в объединенном списке. Дополнительные сведения см. в разделе [Сопоставление схожих данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md).  
  
3.  Чтобы просмотреть дополнительные сведения о схожести, обнаруженной службами DQS, отобразите столбцы со сведениями.  
  
4.  Просмотрите результаты и определите, какие данные следует добавить в репозиторий MDS и какие данные дублируются.  
  
5.  Опубликуйте новые и/или обновленные данных в репозитории MDS.  
  
## <a name="knowledge-bases"></a>Базы знаний  
 Результаты сопоставления, предлагаемые в надстройке, основаны на базе знаний служб DQS.  
  
-   База знаний по умолчанию (DQS Data) создается при установке служб DQS. Если выбрать для использования базу знаний по умолчанию (без добавления политики сопоставления по умолчанию в базу знаний клиента DQS Data Quality), необходимо сопоставить столбцы в листе с доменами в базе знаний, затем присвоить значение веса с выбранными доменами.  
  
-   Для создания новой базы знаний с политикой маршрутов можно использовать клиент DQS, а можно добавить политику сопоставления в базе знаний по умолчанию. В этом случае значения веса определяются уже созданной политикой сопоставления и потребуется только сопоставить столбцы и домены. Дополнительные сведения см. в статье [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
 Дополнительные сведения о базах знаний см. в разделе [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Объедините внешние данные с данными, управляемыми MDS, и подготовьтесь к их сравнению.|[Объединение данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md)|  
|Воспользуйтесь базой набора знаний служб DQS для определения схожести данных.|[Сопоставление схожих данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Обзор импорта данных из Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [Data Matching](../../data-quality-services/data-matching.md)  
  
  

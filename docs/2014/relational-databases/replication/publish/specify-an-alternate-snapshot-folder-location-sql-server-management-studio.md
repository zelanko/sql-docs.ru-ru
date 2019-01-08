---
title: Выбор альтернативного расположения папки моментальных снимков (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6505d78a48b60fba5ed3580b8c00503d1f54ddce
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52815476"
---
# <a name="specify-an-alternate-snapshot-folder-location-sql-server-management-studio"></a>указать местоположение альтернативной папки моментальных снимков (среда SQL Server Management Studio)
  Укажите альтернативное расположение моментальных снимков на странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
### <a name="to-specify-an-alternate-snapshot-location"></a>Указание альтернативной папки моментальных снимков  
  
1.  На странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>** сделайте следующее:  
  
    1.  Выберите **Поместить файлы в следующую папку**, затем нажмите кнопку **Обзор** , чтобы перейти в каталог, или введите путь к каталогу, в который должны сохраняться файлы моментальных снимков.  
  
        > [!NOTE]  
        >  Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать UNC-путь общего каталога, например \\\computername\snapshot. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](../security/secure-the-snapshot-folder.md).  
  
    2.  Снимите флажок **Поместить файлы в папку по умолчанию** , если не требуется, чтобы файлы были помещены в оба расположения.  
  
     Для сжатия файлов моментальных снимков выберите **Сжать файлы моментальных снимков в этом расположении**. Сжатие обычно используется для узкополосных подключений и для альтернативных расположений моментальных снимков на сменных носителях, таких, как компакт-диски.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Альтернативные расположения папки моментальных снимков](../alternate-snapshot-folder-locations.md)   
 [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Указание расположения моментальных снимков по умолчанию (SQL Server Management Studio)](../specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Изменение свойств публикации и статьи](change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../initialize-a-subscription-with-a-snapshot.md)  
  
  

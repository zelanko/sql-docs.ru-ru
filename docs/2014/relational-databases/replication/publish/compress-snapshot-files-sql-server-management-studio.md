---
title: Сжатие файлов моментальных снимков (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c8be85ae97d281113515205fadba9be827492474
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762576"
---
# <a name="compress-snapshot-files-sql-server-management-studio"></a>сжать файлы моментальных снимков (среда SQL Server Management Studio)
  Укажите, что файлы требуется сжать, на странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
### <a name="to-compress-snapshot-files"></a>Сжатие файлов моментальных снимков  
  
1.  На странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>** сделайте следующее:  
  
    1.  Выберите **Поместить файлы в следующую папку**, затем нажмите кнопку **Обзор** , чтобы перейти в каталог, или введите путь к каталогу, в который должны сохраняться файлы моментальных снимков.  
  
        > [!NOTE]  
        >  Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать UNC-путь общего каталога, например \\\computername\snapshot. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](../security/secure-the-snapshot-folder.md).  
  
    2.  Снимите флажок **Поместить файлы в папку по умолчанию** , если не требуется, чтобы файлы были помещены в оба расположения.  
  
        > [!NOTE]  
        >  Если данный флажок установлен, файлы, хранящиеся в папке по умолчанию, не сжимаются. Сжатые файлы можно хранить только в альтернативной папке, указанной на предыдущем шаге.  
  
2.  Выберите **Выполнять сжатие файлов моментальных снимков в этой папке**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](change-publication-and-article-properties.md)   
 [Сжатые моментальные снимки](../compressed-snapshots.md)   
 [Инициализация подписки с помощью моментального снимка](../initialize-a-subscription-with-a-snapshot.md)  
  
  

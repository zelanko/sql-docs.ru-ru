---
title: "Установка компонентов R без доступа к Интернету | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 30
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 21
---
# Установка компонентов R без доступа к Интернету
  Для установки компонентов R, используемых [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , требуется подключение к Интернету для доступа к файлам, которые предоставляются либо центром загрузки Майкрософт, либо другим доверенным узлом. Тем не менее эти компоненты можно установить на сервере без доступа к Интернету, создав их локальные копии, как описано в этом разделе.  
  
  > [!TIP]
  > 
  > Подробное пошаговое руководство по процессу автономной установки см. в блоге [группы консультирования клиентов SQL Server](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).
  
## <a name="installation-on-computers-with-no-internet-access"></a>Установка на компьютеры без доступа к Интернету  
 При выполнении автономной установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не имеет доступа к ссылкам на установку необходимых компонентов R. Чтобы избежать этой проблемы, можно скачать копию установщиков на локальный компьютер и завершить установку, как описано в этом разделе.
 
 Обратите внимание на то, что для компонентов R имеется два установщика: один для Microsoft R Open, а другой для Microsoft R Server. Для использования служб R SQL Server необходимо скачать и запустить оба установщика. Мастер установки SQL Server обеспечит их установку в правильном порядке.


Выпуск  |Ссылка на скачивание  
---------|---------
**SQL Server 2016 RTM**     |           
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)     
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)      
**SQL Server 2016 с накопительным пакетом обновления 1**     |           
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)     
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)      
**SQL Server 2016 с накопительным пакетом обновления 2**     |           
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)     
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)  
**SQL Server 2016 с накопительным пакетом обновления 3**     |           
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab: ](https://go.microsoft.com/fwlink/?LinkId=831785)     
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)  |
**SQL Server 2016 с пакетом обновления 1 (SP1)**     |           
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)     
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)  
**SQL Server 2016 с пакетом обновления 1 (SP1) GDR**     |           
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)     
Microsoft R Server     |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)  

  
**Обновление компонентов R в автономной установке**     

1. Используйте приведенные выше ссылки, чтобы скачать соответствующую версию.
2. Скопируйте файлы CAB в папку на компьютере, в которой будет установлено обновление.
3. После запуска мастера установки SQL Server нажмите кнопку **Принять** на странице лицензирования Microsoft R.  Появится диалоговое окно со ссылками на файлы для скачивания. Введите путь к папке с файлами, которые вы скачали. 
4. Нажмите кнопку **Далее**, чтобы указать, что компоненты доступны, и завершите работу мастера установки SQL Server.
5. При необходимости можно также скачать архивированный исходный код для компонентов с открытым исходным кодом. Дополнительные сведения см. в разделе [Установка служб SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).


> [!IMPORTANT] Если вы скачиваете файлы CAB в процессе установки SQL Server на компьютере с доступом к Интернету, мастер установки определяет местный язык и автоматически меняет язык установщика. 
> 
> Но если вы устанавливаете одну из локализованных версий SQL Server на компьютере без доступа к Интернету и скачиваете установщики R в локальную общую папку, необходимо вручную изменить имена скачиваемых файлов и вставить правильный идентификатор языка установки. 
> 
> Например, если вы устанавливаете японскую версию SQL Server, имя файла SRS_8.0.3.0_1033.cab следует изменить на SRS_8.0.3.0_1041.cab.    
 
  
## <a name="see-also"></a>См. также:  
 [Приступая к работе со службами SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 [Устранение неполадок при установке служб R](../Topic/Troubleshooting%20R%20Services%20Setup.md)  
  
  
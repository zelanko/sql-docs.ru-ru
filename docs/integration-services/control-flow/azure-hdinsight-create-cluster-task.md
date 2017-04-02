---
title: "Задача создания кластера Azure HDInsight | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpcreatecltask.f1"
  - "sql14.dts.designer.afpcreatecltask.f1"
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Задача создания кластера Azure HDInsight
  **Задача создания кластера Azure HDInsight** позволяет пакету служб SSIS создать кластер Azure HDInsight в указанной подписке Azure.  
  
 **Задача создания кластера Azure HDInsight** входит в состав пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure для SQL Server 2016. Пакет дополнительных компонентов можно скачать [отсюда](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
> [!NOTE]  
>  -   Создание кластера HDInsight обычно занимает 10 минут.  
> -   Создание кластера Azure HDInsight и управление им связано с затратами. Дополнительные сведения см. в статье [Цены на HDInsight](http://azure.microsoft.com/en-us/pricing/details/hdinsight/).  
  
 Чтобы добавить **задачу создания кластера Azure HDInsight**, перетащите ее в конструктор служб SSIS и дважды щелкните или щелкните правой кнопкой мыши и выберите пункт **Изменить**, чтобы вызвать диалоговое окно **Azure HDInsight Create Cluster Task Editor** (Редактор задач создания кластера Azure HDInsight).  
  
 Следующая таблица содержит описание полей этого диалогового окна.  
  
|||  
|-|-|  
|**Поле**|**Description**|  
|AzureSubscriptionConnection|Создайте новый или выберите существующий диспетчер соединений подписки Azure, ссылающийся на подписку Azure, в которой размещается кластер HDInsight.|  
|AzureStorageConnection|Выберите существующий диспетчер подключений службы хранилища Azure или создайте диспетчер подключений, который ссылается на учетную запись хранения Azure, которая будет связана с кластером HDInsight.|  
|Местоположение|Определите расположение кластера HDInsight. Кластер нужно создавать в том же расположении, в котором находится служба хранилища Azure.|  
|ClusterName|Укажите имя для создаваемого кластера HDInsight.|  
|ClusterSize|Укажите число узлов, которые должны быть в кластере.|  
|BlobContainer|Укажите имя контейнера хранилища по умолчанию, связанного с кластером HDInsight.|  
|UserName|Укажите имя пользователя, имеющего доступ к кластеру.|  
|Пароль|Укажите пароль для пользователя.|  
|FailIfExists|Укажите, следует ли завершать задачу сбоем, если кластер уже существует.|  
  
> [!NOTE]  
>  Расположения кластера HDInsight и службы хранилища Azure должны совпадать.  
  
  
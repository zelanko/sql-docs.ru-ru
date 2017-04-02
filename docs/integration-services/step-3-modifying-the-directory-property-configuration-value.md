---
title: "Шаг 3. Изменение значения конфигурации свойства Directory | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Шаг 3. Изменение значения конфигурации свойства Directory
В этой задаче предстоит изменить хранимый в файле SSISTutorial.dtsConfig параметр настройки свойства Value переменной уровня пакета `User::varFolderName`. Эта переменная обновляет свойство Directory контейнера "цикл по каждому элементу". Измененное значение будет указывать на папку **Новый образец данных** , созданную в предыдущей задаче. После изменения параметра настройки конфигурации и выполнения пакета свойство Directory будет обновляться этой переменной с использованием значения из файла конфигурации, а не значения из каталога, первоначально заданного в данном пакете.  
  
### Изменение параметра конфигурации для свойства Directory  
  
1.  В приложении «Блокнот» или другом текстовом редакторе найдите и откройте файл конфигурации SSISTutorial.dtsConfig, созданный в предыдущей задаче с помощью мастера настройки пакета.  
  
2.  Измените значение элемента **ConfiguredValue** таким образом, чтобы он соответствовал пути к папке **Новый образец данных** , созданной в предыдущей задаче. Не заключайте этот путь в кавычки. Если папка **Новый образец данных** находится на корневом уровне диска (например, C:\\), то обновляемый файл XML должен выглядеть следующим образом:  
  
    `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
    Конечно, данные заголовка — **GeneratedBy**, **GeneratedFromPackageID**и **GeneratedDate** — в вашем файле будут иными. **Configuration** — элемент, на который необходимо обратить внимание. Свойство **Value** переменной `User::varFolderName` теперь содержит значение C:\New Sample Data.  
  
3.  Сохраните изменения и закройте текстовый редактор.  
  
## Следующая задача занятия  
[Шаг 4. Проверка учебного пакета, созданного на занятии 5](../integration-services/step-4-testing-the-lesson-5-tutorial-package.md)  
  
  
  

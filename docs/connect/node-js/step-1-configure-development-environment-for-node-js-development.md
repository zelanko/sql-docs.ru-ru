---
title: Шаг 1. Настройка среды разработки для Node.js | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 823177f8fef91dda8cf879f6be84ef6706224fad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600242"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Шаг 1. Настройка среды разработки для разработки на Node.js
Необходимо будет настроить среду разработки с предварительные требования для разработки приложения с помощью драйвера Node.js для SQL Server.  Наиболее распространенный метод является использование диспетчера пакетов node (npm), чтобы установить модуль утомительно, но вы можете скачать модуль утомительно непосредственно на [Github](https://github.com/pekim/tedious) при желании.  
  
Обратите внимание на то, что драйвер Node.js использует протокол потока табличных данных, которое включено по умолчанию в SQL Server и базы данных SQL Azure.  Дополнительная настройка не требуется.  
  
## <a name="windows"></a>Windows  
  
1. **Установка диспетчера пакетов Node.js среда выполнения и npm**  
A. Перейдите к [Node.js](https://nodejs.org/en/download/)  
Б. Щелкните соответствующую ссылку msi установщика Windows.   
в. После скачивания запустите файл msi для установки Node.js  
  
2. **Откройте cmd.exe**  
  
3. **Создайте каталог проекта** и перейдите к нему.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Создание проекта узла.**  Чтобы сохранить значения по умолчанию во время создания проектов, нажмите клавишу ВВОД, пока не будет создан проект. В конце этого шага вы увидите файл package.json в каталоге проекта.  
```  
> npm init  
```  
  
5. **Установите модуль tedious в проекте.**  Это реализация протокола TDS, использующего драйвер для связи с SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Открыть терминал**  
  
2. **Установите среду выполнения Node.js**  
```  
>sudo apt-get install node  
```  
3. **Установка npm (диспетчер пакетов node)**  
```  
> sudo apt-get install npm  
```  
4. **Создайте каталог проекта** и перейдите к нему.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Создание проекта узла.**  Чтобы сохранить значения по умолчанию во время создания проектов, нажмите клавишу ВВОД, пока не будет создан проект. В конце этого шага вы увидите файл package.json в каталоге проекта.  
```  
> sudo npm init  
```  
  
6. **Установите модуль tedious в проекте.**  Это реализация протокола TDS, использующего драйвер для связи с SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Установка диспетчера пакетов Node.js среда выполнения и npm**  
A. Перейдите к [Node.js](https://nodejs.org/en/download/)  
Б. Щелкните соответствующую ссылку установщика Mac OS.  
в. После завершения загрузки запустите dmg для установки Node.js  
  
2. **Открыть терминал**  
  
3. **Создайте каталог проекта** и перейдите к нему.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Создание проекта узла.**  Чтобы сохранить значения по умолчанию во время создания проектов, нажмите клавишу ВВОД, пока не будет создан проект. В конце этого шага вы увидите файл package.json в каталоге проекта.  
```  
> npm init  
```  
  
5. **Установите модуль tedious в проекте.**  Это реализация протокола TDS, использующего драйвер для связи с SQL Server.  
```  
> npm install tedious  
```  
  

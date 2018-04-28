---
title: 'Шаг 1: Настройка среды разработки Python pyodbc | Документы Microsoft'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: python
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: 64ce99a11d0942efaaaee2ba70831cd0f5e6b236
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Шаг 1: Настройка среды разработки для pyodbc разработки Python

## <a name="windows"></a>Windows  
Подключитесь к базе данных SQL с помощью Python - pyodbc в Windows:
  
1. **Загрузка установщика Python**  
  Если компьютер не имеет Python установите ее. Go [страница загрузки Python](https://www.python.org/downloads/windows/) и загрузить соответствующий установщик. Для примера при работе в 64-разрядном компьютере, загрузите установщик Python 2.7 или 3.5 (x 64).  
  
2. **Установка Python** после загрузки установщик, выполните следующие действия:. Дважды щелкните файл, чтобы запустить программу установки. Б. Выберите язык и согласиться с условиями. в. Следуйте инструкциям на экране и Python должна быть установлена на компьютере. г. Можно проверить, установлена, перейдите к C:\Python27 или C:\Python35 и запустите python - v или py - v (для 3.x) Python 
      
3. [**Установка драйвера Microsoft ODBC**](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)
  
4. **Откройте cmd.exe от имени администратора**     

5. **Установка с помощью pip - pyodbc Python package manager**
```  
> cd C:\Python27\Scripts>  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Подключитесь к базе данных SQL с помощью Python - pyodbc Ubuntu и RedHat:
  
1. **Откройте терминалов**  

2. **Установка Microsoft ODBC Driver 13 для Linux** для Ubuntu 15.04 + 
``` 
> sudo su  
> wget https://gallery.technet.microsoft.com/ODBC-Driver-13-for-Ubuntu-b87369f0/file/154097/2/installodbc.sh  
> sh installodbc.sh  
```   

  Для RedHat 6,7 
``` 
> sudo su 
> wget https://gallery.technet.microsoft.com/ODBC-Driver-13-for-SQL-8d067754/file/153653/4/install.sh 
> sh install.sh 
```  
  
3.  **Установить pyodbc**  
```  
> sudo -H pip install pyodbc
```

<h1 align="center"> 2022 SW Education for Vietnamese Students in Korea </h1>
<h1 align="center"> Assignment Report </h1>

**Author: Do Truong Dong** <br>
Email: <truongdong.sju@gmail.com>

# 1. Topic chosing
I chose topic **#2** for my study. The URL to access the data [here](https://www.data.go.kr/data/15098931/openapi.do).

### <span style="color:red">Korean</span>:
  **유기견보호** \
농림축산식품부 농림축산검역본부 동물보호관리시스템 유기동물 조회 서비스: 동물보호관리시스템 유기동물 정보를 조회할 수 있다.

### <span style="color:blue">English</span>:
Ministry of Agriculture, Food and Rural Affairs, Agriculture, Forestry and Livestock Quarantine Headquarters: Animal protection management system abandoned animal information inquiry service.


# 2. Data Overview
This is a service that allows us to inquire information on abandoned animals of the animal protection management system and provides city and county inquiry API, city and county inquiry API, shelter inquiry API, and breed inquiry API so that you can inquire about additional information included in abandoned animal information.

The guide for using this Animal Protection Management System Open API can be accessed [here](https://github.com/TruongDong-Do/2022_VNKR_SW_Training/blob/7ad04cd2ed89c9f83bb7f09fc8eebdbea0fcecc4/%EB%8F%99%EB%AC%BC%EB%B3%B4%ED%98%B8%EA%B4%80%EB%A6%AC%EC%8B%9C%EC%8A%A4%ED%85%9C%20Open%20API%20%ED%99%9C%EC%9A%A9%EA%B0%80%EC%9D%B4%EB%93%9C%20-%20%EC%9C%A0%EA%B8%B0%EB%8F%99%EB%AC%BC%20%EC%A1%B0%ED%9A%8C%20%EC%84%9C%EB%B9%84%EC%8A%A4.docx). In this file, we can find all the information about this ***Abandoned Animal Inquiry Service*** consist of data properties, data inquiry link, data inquiry code.

<p align="center">
 <img src="images/data_info.png" alt="Data information" style="width:600px;"/>
</p>
<p align = "center">
 <em>Figure 1: The basic and service information of the data.</em>
</p>

### The Java code to request the data
```java
/* Java 1.8 sample code */

import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;
import java.net.URLEncoder;
import java.io.BufferedReader;
import java.io.IOException;

public class ApiExplorer {
    public static void main(String[] args) throws IOException {
        StringBuilder urlBuilder = new StringBuilder("http://apis.data.go.kr/1543061/abandonmentPublicSrvc/sido"); /*URL*/
        urlBuilder.append("?" + URLEncoder.encode("serviceKey","UTF-8") + "=servicekey"); /*Service Key*/
        urlBuilder.append("&" + URLEncoder.encode("numOfRows","UTF-8") + "=" + URLEncoder.encode("3", "UTF-8"));
        urlBuilder.append("&" + URLEncoder.encode("pageNo","UTF-8") + "=" + URLEncoder.encode("1", "UTF-8")); /*PageNumber*/
        urlBuilder.append("&" + URLEncoder.encode("_type","UTF-8") + "=" + URLEncoder.encode(" ", "UTF-8")); /*xml (default) or json*/
        URL url = new URL(urlBuilder.toString());
        HttpURLConnection conn = (HttpURLConnection) url.openConnection();
        conn.setRequestMethod("GET");
        conn.setRequestProperty("Content-type", "application/json");
        System.out.println("Response code: " + conn.getResponseCode());
        BufferedReader rd;
        if(conn.
            rd = new BufferedReader(new InputStreamReader(conn.getInputStream()));
        } else {
            rd = new BufferedReader(new InputStreamReader(conn.getErrorStream()));
        }
        StringBuilder sb = new StringBuilder();
        String line;
        while ((line = rd.readLine()) != null) {
            sb. append(line);
        }
        rd.close();
        conn.disconnect();
        System.out.println(sb.toString());
    }
}
```

# 3. Solution for required tasks

"Data"

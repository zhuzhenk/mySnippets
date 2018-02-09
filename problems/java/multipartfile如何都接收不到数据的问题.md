```
1.一般情况下 
 <bean id="multipartResolver"   class="org.springframework.web.multipart.commons.CommonsMultipartResolver" >
		  <property name="maxUploadSize">
	          <value>104857600</value>
	       </property>
	        <property name="maxInMemorySize">
	            <value>4096</value>
	        </property>
	         <property name="defaultEncoding">
	            <value>utf-8</value>
	        </property>
    </bean>
2。然后再使用@RequestParam("file") MultipartFile[] file即可获取到了，但是今天使用dropzon图片上传插件的时候们，不管怎样都上传不了数据了，、
到只得原因是dropzon有一个multipart的属性，false就好了，
3。原因是<form id="dropzone" class="dropzone" enctype="multipart/form-data">
                <input type="hidden" name="articleId" id="articleId" value="${articleId}"/>
                <div class="fallback">
                    <input name="file" type="file" multiple
                           accept="image/jpg,image/jpeg,image/png,image/bmp,image/gif,image/x-icon">
                </div>
                <div class="dz-message">
                    <p>将文件拖至此处或点击上传.</p>
                    <p>
                        <span style="font-size: 16px; color: #d0d0d0;">一次最多可以上传5个文件</span>
                    </p>
                </div>
            </form>
            提交的时候，file被转换为了file[0],file[1]等一些列的字符串，
4。去掉dropzone的multi属性之后，请求被拆分成了多个请求，每个请求发送一个文件，但是后台看不到区别，
```




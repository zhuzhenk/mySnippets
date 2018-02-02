```
package com.zzk.magic.utiles;

import lombok.Getter;
import lombok.NonNull;
import org.springframework.beans.BeansException;
import org.springframework.context.ApplicationContext;
import org.springframework.context.ApplicationContextAware;
import org.springframework.stereotype.Component;

@Component
public class ContextUtil implements ApplicationContextAware {

    @Getter
    private static volatile ApplicationContext context = null;

    /**
     * 加载Spring配置文件时，如果Spring配置文件中所定义的Bean类实现了ApplicationContextAware 接口，那么在加载Spring配置文件时，会自动调用ApplicationContextAware 接口中的
     * public void setApplicationContext(ApplicationContext context) throws BeansException
     * & 方法，获得ApplicationContext对象
     *
     * @param applicationContext
     * @throws BeansException
     */
    @Override
    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {
        context = applicationContext;
    }

    /**
     * 获取bean
     *
     * @param clazz
     * @param beanName
     * @param <T>
     * @return
     */
    public static <T> T getBean(@NonNull Class<T> clazz, @NonNull String beanName) {
        return (T) context.getBean(beanName);
    }
}

```




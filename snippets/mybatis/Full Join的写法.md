```
SELECT * from (
		SELECT m.static_date, IFNULL(m.m_count,0) as m_count, IFNULL(p.p_count,0) as p_count from
		( SELECT DATE_FORMAT(create_time,"%Y-%m-%d") as static_date,count(1) as m_count from member GROUP BY
		DATE_FORMAT(create_time,"%Y-%m-%d") ) m LEFT JOIN
		( SELECT DATE_FORMAT(create_time,"%Y-%m-%d") as static_date,count(1) as p_count from provider GROUP BY
		DATE_FORMAT(create_time,"%Y-%m-%d") ) p ON (m.static_date = p.static_date)

		UNION

		SELECT p.static_date, IFNULL(m.m_count,0) as m_count, IFNULL(p.p_count,0) as p_count from
		( SELECT DATE_FORMAT(create_time,"%Y-%m-%d") as static_date,count(1) as m_count from member GROUP BY
		DATE_FORMAT(create_time,"%Y-%m-%d") ) m RIGHT JOIN
		( SELECT DATE_FORMAT(create_time,"%Y-%m-%d") as static_date,count(1) as p_count from provider GROUP BY
		DATE_FORMAT(create_time,"%Y-%m-%d") ) p ON (m.static_date = p.static_date)
		) p
		<where>
			<!-- 检索 -->
			<if test="beginDate != null and beginDate != ''">
				and date_format(p.static_date,'%Y-%m-%d') &gt;= #{beginDate}
			</if>
			<if test="endDate != null and endDate != ''">
				and date_format(p.static_date,'%Y-%m-%d') &lt;= #{endDate}
			</if>
		</where>
		ORDER BY p.static_date DESC
		
		
		mysql 没有full join ，用这个hack写法来代替
```




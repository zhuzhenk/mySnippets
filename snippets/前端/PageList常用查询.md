```
<!-- 客户池列表 -->
	<select id="customerPoolPageList" parameterType="ezuiPage" resultType="pd" useCache="false">
		select
		    <include refid="Base_Column_List_Text" />
		from 
			customer_pool
		where 1=1
		  <if test="pd.customerStatus != ''">
            and customer_status = #{pd.customerStatus}
          </if>
		  <if test="pd.customerStatus == ''">
			and (customer_status IS NULL OR TRIM(customer_status) = #{pd.customerStatus} )
		  </if>

		<if test="pd.customerName!= null and pd.customerName!= ''">
            and customer_name = #{pd.customerName}
          </if> 
          <if test="pd.labels != null and pd.labels != ''">
            and FIND_IN_SET(#{pd.labels},labels)
          </if> 
          <if test="pd.memo != null and pd.memo != ''">
            and memo LIKE concat('%' ,#{pd.memo},'%')
          </if>
          <if test="pd.callNum != null and pd.callNum != ''">
            and call_num = #{pd.callNum}
          </if> 
          <if test="pd.callStatus != null and pd.callStatus != ''">
            and call_status = #{pd.callStatus}
          </if> 
          <if test="pd.dataProvider != null and pd.dataProvider != ''">
            and data_provider = #{pd.dataProvider}
          </if>
           <if test="pd.retainStatus != null and pd.retainStatus != ''">
            and retain_status = #{pd.retainStatus}
          </if>
          <if test="pd.customerGrade != null and pd.customerGrade != ''">
            and customer_grade = #{pd.customerGrade}
          </if>
          <if test="pd.rStartTime != null and pd.rStartTime != ''">
			and latest_contact_time &gt;= str_to_date(#{pd.rStartTime}, '%Y-%m-%d')
		  </if>
		  <if test="pd.rEndTime != null and pd.rEndTime != ''">
			and latest_contact_time &lt; date_add(str_to_date(#{pd.rEndTime}, '%Y-%m-%d'), INTERVAL 1 DAY)
		  </if>
		   <if test="pd.yStartTime != null and pd.yStartTime != ''">
			and return_visit_time &gt;= str_to_date(#{pd.yStartTime}, '%Y-%m-%d')
		  </if>
		  <if test="pd.yEndTime != null and pd.yEndTime != ''">
			and return_visit_time &lt; date_add(str_to_date(#{pd.yEndTime}, '%Y-%m-%d'), INTERVAL 1 DAY)
		  </if>
		   <if test="pd.cStartTime != null and pd.cStartTime != ''">
			and create_time &gt;= str_to_date(#{pd.cStartTime}, '%Y-%m-%d')
		  </if>
		  <if test="pd.cEndTime != null and pd.cEndTime != ''">
			and create_time &lt; date_add(str_to_date(#{pd.cEndTime}, '%Y-%m-%d'), INTERVAL 1 DAY)
		  </if>
          <if test="pd.groupId != null and pd.groupId != ''">
            and group_id = #{pd.groupId}
          </if>
          <if test="pd.saId != null and pd.saId != ''">
            and sa_id = #{pd.saId}
          </if>
          <if test="pd.teamId != null and pd.teamId != ''">
            and team_id = #{pd.teamId}
          </if>
		  order by auto_recycle_time,customer_grade desc,call_status asc,customer_id asc
		  <!-- 排序：马上要回收的，客户级别高的在前面 -->
	</select>
```




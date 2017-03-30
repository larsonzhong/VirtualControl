# Android虚拟摇杆
安卓虚拟摇杆，全方位控制

##使用方法

##①attr中定义自定义参数

      <!-- areaBackground 设置区域背景
         rockerBackground 设置摇杆的样式
         rockerScale 设置摇杆的相对于背景的比例
         rockerSpeedLevel 设置当前位置相对于中心点的距离的比例  如：10  则中心点到边缘的距离分为10分 越靠外数值越大0-10
         rockerCallBackMode 有变化就回调，或者是方向改变才会回调-->
    <declare-styleable name="RockerView">
        <attr name="areaBackground" format="color|reference" />
        <attr name="rockerBackground" format="color|reference" />
        <attr name="rockerScale" format="float"/>
        <attr name="rockerSpeedLevel" format="integer" />
        <attr name="rockerCallBackMode">
            <flag name="CALL_BACK_MODE_MOVE" value="0" />
            <flag name="CALL_BACK_MODE_STATE_CHANGE" value="1" />
        </attr>
    </declare-styleable>
    
##②复制RockerView到项目中

##③使用摇杆控件

    <com.larsonzhong.virtualcontrol.RockerView
        android:id="@+id/my_rocker"
        android:layout_width="200dp"
        android:layout_height="200sp"
        android:background="@color/colorPrimary"
        app:areaBackground="@mipmap/rocker_base"
        app:rockerBackground="@mipmap/rocker"
        app:rockerSpeedLevel="10"
        app:rockerCallBackMode="CALL_BACK_MODE_STATE_CHANGE"
        app:rockerScale="0.5" />
        
###③事件回调
   
     mRockerView.setOnShakeListener(DIRECTION_8, new RockerView.OnShakeListener() {
            @Override
            public void onStart() {

            }

            @Override
            public void direction(RockerView.Direction direction) {
                if (direction == RockerView.Direction.DIRECTION_CENTER){
                    mTvShake.setText("当前方向：中心");
                }else if (direction == RockerView.Direction.DIRECTION_DOWN){
                    mTvShake.setText("当前方向：下");
                }else if (direction == RockerView.Direction.DIRECTION_LEFT){
                    mTvShake.setText("当前方向：左");
                }else if (direction == RockerView.Direction.DIRECTION_UP){
                    mTvShake.setText("当前方向：上");
                }else if (direction == RockerView.Direction.DIRECTION_RIGHT){
                    mTvShake.setText("当前方向：右");
                }else if (direction == RockerView.Direction.DIRECTION_DOWN_LEFT){
                    mTvShake.setText("当前方向：左下");
                }else if (direction == RockerView.Direction.DIRECTION_DOWN_RIGHT){
                    mTvShake.setText("当前方向：右下");
                }else if (direction == RockerView.Direction.DIRECTION_UP_LEFT){
                    mTvShake.setText("当前方向：左上");
                }else if (direction == RockerView.Direction.DIRECTION_UP_RIGHT){
                    mTvShake.setText("当前方向：右上");
                }
            }

            @Override
            public void onFinish() {

            }
        });
        mRockerView.setOnAngleChangeListener(new RockerView.OnAngleChangeListener() {
            @Override
            public void onStart() {

            }

            @Override
            public void angle(double angle) {
                mTvAngle.setText("当前角度："+angle);
            }

            @Override
            public void onFinish() {

            }
        });

        mRockerView.setOnDistanceLevelListener(new RockerView.OnDistanceLevelListener() {
            @Override
            public void onDistanceLevel(int level) {
                mTvLevel.setText("当前距离级别："+level);
            }
        });
​

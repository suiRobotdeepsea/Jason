//轮式机器人的线速度公式

//位姿结构体
typedef struct
{
	float x;
	float y;
	float theta;
}

//更新位姿
void update_position(Pose* p, float v_left, float v_right, float dt, float wheelbase)
{
    	float v = (v_left + v_right) / 2.0;          // 线速度  
    	float omega = (v_right - v_left) / wheelbase; // 角速度  
    	p->x += v * cos(p->theta) * dt;             // x方向积分  
    	p->y += v * sin(p->theta) * dt;             // y方向积分  
    	p->theta += omega * dt;                      // 角度积分  
}


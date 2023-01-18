编写顶点你着色器，主要是 定义接收位置大小信息的变量 和 转化坐标位置
编写片元着色器，主要是 定义获取颜色信息的变量 和 转化颜色信息

获取绘图上下文
创建顶点和片元着色器，createShader指定着色器类型创建，之后需要shaderSource把着色器代码塞进去，之后compileShader编译
创建着色器程序，createProgram创建，attachShader将着色器贴在程序上，linkProgram链接一下程序
使用着色器程序useProgram（可能链接了很多个，需要指定一个）

获取着色器中的变量getAttribLocation(program, 'a_Position')/getUniformLocation

创建缓冲区createBuffer
绑定为当前缓冲区bindBuffer(gl.ARRAY_BUFFER, buffer)
使用 gl.bufferData 将类型化后的数组复制到缓冲区（gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(positions), gl.STATIC_DRAW);）

指定从buffer取数据的规则vertexAttribPointer（gl.vertexAttribPointer(a_Position, size, type,normalize, stride, offset);）

监听点击事件，触发条件需要重新将数据复制到缓冲区bufferData
将颜色赋值gl.uniform4f(u_Color, color.r, color.g, color.b, color.a);

设置清空画布的颜色gl.clearColor(0, 0, 0, 1);
绘制前先清除画布gl.clear(gl.COLOR_BUFFER_BIT);
gl.drawArrays(primitiveType, drawOffset, positions.length / 2);
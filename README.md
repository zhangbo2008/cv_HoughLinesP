# cv_HoughLinesP
hopf直线检测最优代码



binary = 255-binary #==========背景色是白色, 东西是黑色.我们要的边缘是黑色的边,也就是边缘上的色素是黑色的.这样保证我们hopf得到的点也是踩在我们要的区域上的.

res = cv2.Laplacian(binary, cv2.CV_8U)


edges = cv2.convertScaleAbs(res)  # 转换为uint8
cv2.imwrite('13里面的canny边缘化图片2.png', edges)
if 0:
	if debug:
		cv2.imwrite('binary2.png', binary)
	edges = cv2.Canny(binary, 100, 200)
	# 霍夫曼直线检测
	cv2.imwrite('13里面的canny边缘化图片.png', edges)

gao = edges.shape[0]
chang = edges.shape[1]

lines = cv2.HoughLinesP(edges, 1, 0.01*np.pi / 180, round((gao+chang)/40), minLineLength=(
	gao+chang)/20, maxLineGap=(gao+chang)/20)  # 0.01*pi是调优过的参数!!!!!!!!
fffff = tmp.copy()

# '카카오미니는 어떻게 스무고개 정답을 맞출까' 칼럼 시뮬레이션  
https://brunch.co.kr/@kakao-it/157

```java
	static void soomoogogaeSimul() {
		int N = 6;
		double[][] likelihood = { { 0.9, 0.9, 0.1, 0.9, 0.1, 0.1 }, { 0.8, 0.9, 0.1, 0.2, 0.1, 0.2 },
				{ 0.1, 0.1, 0.9, 0.1, 0.9, 0.2 }, { 0.1, 0.1, 0.1, 0.1, 0.8, 0.8 }, { 0.1, 0.9, 0.9, 0.1, 0.9, 0.1 } };
		double[] posterior = { 0.2, 0.2, 0.1, 0.1, 0.1, 0.1 };
		double[] buf = new double[N];

		boolean[] choice = { true, true, false, false, true };

		double numerator;
		double denominator = 0;
		double sum = 0;
		double likeli;

		for (int k = 0; k < likelihood.length; k++) {
			for (int i = 0; i < N; i++) {
				likeli = likelihood[k][i];
				if (!choice[k]) {
					likeli = (1 - likelihood[k][i]);
				}
				numerator = likeli * (posterior[i]) * 0.8;
				denominator = 0;
				for (int j = 0; j < N; j++) {
					likeli = likelihood[k][j];
					if (!choice[k]) {
						likeli = (1 - likelihood[k][j]);
					}
					sum = (likeli * (posterior[j]));
					denominator += sum;
				}
				buf[i] = numerator / denominator;
			}
			for (int i = 0; i < N; i++) {
				posterior[i] = buf[i];
				System.out.printf("%.3f ", buf[i]);
			}
			System.out.println();
		}

		System.out.println();
	}

```

![image](https://user-images.githubusercontent.com/12610035/142224332-37c6e555-241c-44ab-97f4-4e5120d308d8.png)

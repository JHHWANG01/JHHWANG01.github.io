
---

layout:post
title: hello Algorithm

---


Java Basic Sort Algorithm
=====
## select

 ``` java 
 for(int i=0; i<arr.length-1 ; i++) {
			for(int j=i+1; j<arr.length; j++) {
				if(arr[i] > arr[j]) {
					int tmp = arr[i];
					arr[i] = arr[j];
					arr[j] = tmp;
				}
			}
			
		}
  ```

## bubble
```java
for(int i = arr.length; i > 0 ; i—) {
			for(int j =0; j<i-1; j++) {
				if(arr[j]>arr[j+1]) {
					int tmp = arr[j];
					arr[j] = arr[j+1];
					arr[j+1] = tmp;
				}
			}
		}
```
 
## insertion

```java
for(int i = 1; i<arr.length; i++) {
			int tmp = arr[i];
			for(j = i-1; j>=0 && tmp <arr[j]; j—) {
				arr[j+1] = arr[j];
			}
			arr[j+1] = tmp;
		}
```

### Contact me

[deert101@gmail.com](mailto:email@domain.com)



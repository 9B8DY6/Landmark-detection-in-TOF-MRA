# Landmark-detection-in-TOF-MRA
뇌혈관 정량적 분석을 위한 첫걸음

뇌혈관 정량적 분석을 위해 뇌혈관의 landmark를 찍어서 이를 detect하는 과정을 진행해보았다.
1. CNN을 이용한 regression적인 방법

2. GNN을 이용한 방법(reference : Structured Landmark Detection via Topology-Adapting Deep Graph Learning; 	arXiv:2004.08190 [cs.CV])

2번의 방법은 landmark로 보는 node들 간의 관계성이 매우 중요해서 점이 많으면 의미가 있는 결과가 나올 것으로 기대한다.
*그러나 2번을 코드 빌리는 것 없이 나만의 코딩으로 만들었다는 것에 의의를 둔다. *
점의 개수가 작기 때문에 1번이 충분히 좋은 결과가 나올 수 있다.


### Path 사용 패턴
DATA_DIR = Path("../data/raw")
csv_files = list(DATA_DIR.glob("*.csv"))

DATA_PATH = csv_files[0]
df = pd.read_csv(DATA_PATH, low_memory = False)

*csv 파일 row-column 수 확인 : .shape
*csv 파일 정보 : .info()
*앞부분 일부만 보여주기 : df.head()
*열 value 통계 : df[""].describe()
*df["column1"] : column1 열 만 가져오기 -> only 행.
*df["column1"].value_counts(dropna=False) : column1 열에 value 별로 몇개있는지 제공
*df1 = df[df["column1"] == "value1"].copy() -> column1의 값이 value1인 행만 추출하기

.groupby("")
- groupby는 단독으로 아무 기능을 하지 못한다.  뒤에 집계함수가 붙어야됨 ex) .size() -> group별 행 개수 세기.
- groupby("").size() -> group나누고, 그룹별 행데이터 출력.
- .groupby("")[""] : groupby 한 상태에서 [""]열만 추출
- groupby("")[""].mean() -> 해당 열의 평균값 구하기.

*.copy() : shallow copy
*필요한 행만 추출 : df1 = df[df["colum1"].isin(list1)].copy()
*필요한 column만 추출 : 
sol1) raw_df[["column1", "column2", "column3"]]
sol2) selected_cols = ["column1", "column2", "column3"]
new_df = raw_df[selected_cols].copy()

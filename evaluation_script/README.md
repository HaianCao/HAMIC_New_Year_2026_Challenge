# Đánh giá (Evaluation)

## Format

Trước khi sử dụng script đánh giá, hãy đảm bảo cả data dự đoán (prediction) và data đáp án (gold) tuân thủ đúng định dạng sau.

Đối với ALGO Task (VRP):
- Dataset (Gold) là file text (`dataset.txt`) theo định dạng đặc tả của bài toán (Vehicle, Order).
- Prediction data là file CSV chứa các cột: `[ID, Test, Vehicle_ID, Order_ID, Type, Stop_Order]`

Đối với CV Task:
- Gold data là file CSV chứa các cột: `[ID, Age]`
- Prediction data là file CSV chứa các cột: `[ID, Age]`

Đối với NLP Task:
- Gold data là file CSV chứa các cột: `[ID, Emotion]`
- Prediction data là file CSV chứa các cột: `[ID, Emotion]`

Lưu ý:
1. Các cột không liên quan đến việc đánh giá sẽ bị bỏ qua.
2. Các giá trị bị thiếu (missing values) hoặc sai định dạng sẽ gây lỗi.

---

## Hướng dẫn sử dụng (Usage)

Script đánh giá cung cấp các hàm chính:
- `cv_task_score`: tính điểm RMSE cho CV Task
- `nlp_task_score`: tính điểm Macro F1 cho NLP Task
- `algo_task_score`: tính điểm hiệu quả Mean Efficiency Score cho ALGO Task

Cài đặt các thư viện cần thiết:
```bash 
pip install -r requirements.txt
```

Nếu bạn chạy trên Jupyter Notebook, hãy import và sử dụng như sau:
```python
# Ví dụ chạy đánh giá
cv_score = cv_task_score('path/to/gold.csv', 'path/to/pred.csv')
nlp_score = nlp_task_score('path/to/gold.csv', 'path/to/pred.csv')
algo_score = algo_task_score('path/to/dataset.txt', 'path/to/pred.csv')
```
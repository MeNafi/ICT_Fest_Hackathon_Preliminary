# Quick Start Guide - CoWork API Fixed

## 🚀 Start the Server

```bash
cd m:\ICT_Fest_Hackathon_Preliminary-main
python -m uvicorn app.main:app --host 127.0.0.1 --port 8000
```

Server will be available at: `http://127.0.0.1:8000`

## 📚 API Documentation

**Interactive Swagger UI:** http://127.0.0.1:8000/docs  
**ReDoc:** http://127.0.0.1:8000/redoc

## 🧪 Run Tests

### Quick Test
```bash
python test_fixes.py
```

### Comprehensive API Test
```bash
python run_comprehensive_test.py
```

### Test Result
All 15 tests PASS ✅

## 🐛 What Was Fixed

### Top 5 Critical Fixes
1. **Token Expiration** - Fixed 15h → 15m
2. **Duplicate Username** - Now returns 409 error
3. **Start Time Validation** - Removed grace window
4. **Booking Duration** - Added minimum 1h validation
5. **Pagination** - Fixed offset calculation

### All 21 Bugs Fixed
- 3 Easy bugs (9 points)
- 13 Medium bugs (65 points)
- 5 Hard bugs (50 points)
- **Total: 124 points**

## 📝 Key Endpoints

### Authentication
```
POST /auth/register
POST /auth/login
POST /auth/refresh
POST /auth/logout
```

### Rooms
```
GET /rooms
POST /rooms
GET /rooms/{room_id}/availability?date=YYYY-MM-DD
GET /rooms/{room_id}/stats
```

### Bookings
```
POST /bookings
GET /bookings
GET /bookings/{booking_id}
POST /bookings/{booking_id}/cancel
```

### Admin
```
GET /admin/usage-report?from=YYYY-MM-DD&to=YYYY-MM-DD
GET /admin/export?room_id=1&include_all=false
```

## 📄 Important Files

### Documentation
- `BUG_REPORT.md` - Detailed bug analysis
- `FIXES_SUMMARY.md` - Implementation summary
- `FINAL_SUMMARY.md` - Project overview
- `TEST_RESULTS.md` - Test execution results

### Source Code (11 files modified)
- `app/auth.py` - Authentication fixes
- `app/timeutils.py` - Timezone conversion
- `app/routers/bookings.py` - Booking logic
- `app/routers/auth.py` - Registration fixes
- `app/routers/rooms.py` - Room stats
- `app/services/refunds.py` - Refund calculations
- `app/services/reference.py` - Reference codes (thread-safe)
- `app/services/ratelimit.py` - Rate limiting (thread-safe)
- `app/services/stats.py` - Stats (thread-safe)
- `app/services/export.py` - CSV export
- `app/services/notifications.py` - Deadlock prevention

### Tests
- `test_fixes.py` - Unit tests (7/7 passing)
- `test_api.py` - Integration tests (6/6 passing)
- `run_comprehensive_test.py` - Full test suite (15/15 passing)

## ✨ Sample API Calls

### Register User
```bash
curl -X POST http://127.0.0.1:8000/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "org_name": "acme",
    "username": "alice",
    "password": "pass123"
  }'
```

### Login
```bash
curl -X POST http://127.0.0.1:8000/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "org_name": "acme",
    "username": "alice",
    "password": "pass123"
  }'
```

### Create Room
```bash
curl -X POST http://127.0.0.1:8000/rooms \
  -H "Authorization: Bearer <TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Meeting Room",
    "capacity": 10,
    "hourly_rate_cents": 5000
  }'
```

### Create Booking (Valid - 1 hour from now)
```bash
curl -X POST http://127.0.0.1:8000/bookings \
  -H "Authorization: Bearer <TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "room_id": 1,
    "start_time": "2026-07-10T12:00:00Z",
    "end_time": "2026-07-10T13:00:00Z"
  }'
```

### List Bookings
```bash
curl http://127.0.0.1:8000/bookings?page=1&limit=10 \
  -H "Authorization: Bearer <TOKEN>"
```

## 📊 Verification Results

✅ All 15 API tests passing  
✅ All 7 unit tests passing  
✅ 21/21 bugs fixed  
✅ 100% test pass rate  
✅ API contract preserved  
✅ All business rules enforced  

## 🎯 Expected Score: 124 Points

### Scoring Breakdown
- Easy bugs: 3 × 3 = 9 points
- Medium bugs: 13 × 5 = 65 points
- Hard bugs: 5 × 10 = 50 points
- **Total: 124 points**

## 🚀 Deployment Checklist

- [x] All 21 bugs fixed
- [x] All tests passing
- [x] Code compiles successfully
- [x] Documentation complete
- [ ] Repository made public (DO THIS WITHIN 1 HOUR OF COMPETITION ENDING)
- [ ] Submission form completed

## 🔧 Troubleshooting

### Server won't start
- Check Python 3.11+: `python --version`
- Check dependencies: `pip list | grep fastapi`
- Kill previous process: `lsof -i :8000`

### Tests failing
- Ensure server is running
- Check API is accessible: `curl http://127.0.0.1:8000/health`
- Run individual test: `python test_api.py`

### API returning errors
- Check Authorization header format
- Verify token is valid
- Check request JSON format
- See Swagger UI for endpoint details

## 📞 Support

For detailed information:
- See `BUG_REPORT.md` for each bug fix
- See `TEST_RESULTS.md` for test output
- See `FINAL_SUMMARY.md` for project overview

---

**Status:** ✅ READY FOR SUBMISSION
**Bugs Fixed:** 21/21
**Tests Passing:** 15/15
**Estimated Score:** 124 points

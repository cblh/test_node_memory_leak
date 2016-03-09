### node内存泄露
TODO
FATAL ERROR: CALL_AND_RETRY_LAST Allocation failed - process out of memory

卧槽，我就调用了一下mogoose API save()，就内存泄露了
这个问题大家怎么看

    DistTest.findOne({_id:data.editId}, function (err, record) {
        if (!err && record) {
            function cb() {
                record.name = data.name;
                record.save();
                callback(null, record);
            }
            cb();
        } else {
            callback(err);
        }
    });
    return;

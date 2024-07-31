![Screenshot 2024-07-30 180410](https://github.com/user-attachments/assets/adbf6ff6-6174-4f06-beaa-7d50c611549d)
![Screenshot 2024-07-30 180347](https://github.com/user-attachments/assets/1d7679a0-08bf-4706-848b-d93830d856d1)
![Screenshot 2024-07-30 180316](https://github.com/user-attachments/assets/3f445e82-809e-475c-8f2b-9f171b4ba270)
![Screenshot 2024-07-30 175509](https://github.com/user-attachments/assets/a978896d-ee27-4332-a562-b97005c4e585)
![Screenshot 2024-07-30 180410](https://github.com/user-attachments/assets/6707d5ba-9eb4-4174-ab79-a0661cb9b640)
![Screenshot 2024-07-30 180400](https://github.com/user-attachments/assets/26428efb-5378-44d8-8201-25f5b3885430)


<menu xmlns:android="http://schemas.android.com/apk/res/android">
 <item
 android:id="@+id/action_add_note"
 android:title="Add Note"
 android:orderInCategory="100"
 android:showAsAction="always" />
 <item
 android:id="@+id/action_view_notes"
 android:title="View Notes"
 android:orderInCategory="100"
 android:showAsAction="never" />
</menu>

<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
 xmlns:app="http://schemas.android.com/apk/res-auto"
 xmlns:tools="http://schemas.android.com/tools"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 tools:context=".MainActivity">
 <com.google.android.material.appbar.AppBarLayout
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar">
 <androidx.appcompat.widget.Toolbar
 android:id="@+id/toolbar"
 android:layout_width="match_parent"
 android:layout_height="?attr/actionBarSize"
 android:background="?attr/colorPrimary"
 app:popupTheme="@style/ThemeOverlay.AppCompat.Light" />
 </com.google.android.material.appbar.AppBarLayout>
 <include layout="@layout/content_main" />
 <com.google.android.material.floatingactionbutton.FloatingActionButton
 android:id="@+id/fab"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_gravity="bottom|end"
 android:layout_margin="@dimen/fab_margin"
 android:src="@android:drawable/ic_input_add" />
</androidx.coordinatorlayout.widget.CoordinatorLayout>
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:orientation="vertical"
 android:padding="16dp">
 <androidx.recyclerview.widget.RecyclerView
 android:id="@+id/recyclerView"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:layout_marginTop="8dp" />
</LinearLayout>

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:orientation="vertical"
 android:padding="16dp">
 <EditText
 android:id="@+id/etTitle"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:hint="Title" />
<EditText
 android:id="@+id/etContent"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:hint="Content"
 android:layout_marginTop="8dp"
 android:inputType="textMultiLine"
 android:minLines="3" />
 <Spinner
 android:id="@+id/spinnerCategory"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:layout_marginTop="8dp" />
 <Button
 android:id="@+id/btnAddNote"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:text="Add Note"
 android:layout_marginTop="16dp" />
 </LinearLayout>


 <?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:orientation="vertical"
 android:padding="16dp">
 <EditText
 android:id="@+id/etTitle"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:hint="Title" />
 <EditText
 android:id="@+id/etContent"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:hint="Content"
 android:layout_marginTop="8dp"
 android:inputType="textMultiLine"
 android:minLines="3" />
 <Spinner
android:id="@+id/spinnerCategory"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:layout_marginTop="8dp" />
 <Button
 android:id="@+id/btnAddNote"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:text="Add Note"
 android:layout_marginTop="16dp" />
</LinearLayout>
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:orientation="vertical"
 android:padding="8dp">
 <TextView
 android:id="@+id/tvTitle"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:textStyle="bold"
 android:textSize="16sp" />
<TextView
 android:id="@+id/tvContent"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginTop="4dp" />
 <TextView
 android:id="@+id/tvCategory"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginTop="4dp"
 android:textStyle="italic" />
</LinearLayout>



package com.example.notesapp
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.fragment.app.DialogFragment
import androidx.recyclerview.widget.LinearLayoutManager
import com.example.notesapp.databinding.ActivityMainBinding
class MainActivity : AppCompatActivity() {
 private lateinit var binding: ActivityMainBinding
 private val notes = mutableListOf<Note>()
 override fun onCreate(savedInstanceState: Bundle?) {
 super.onCreate(savedInstanceState)
 binding = ActivityMainBinding.inflate(layoutInflater)
 setContentView(binding.root)
 setSupportActionBar(binding.toolbar)
 binding.recyclerView.layoutManager = LinearLayoutManager(this)
 binding.recyclerView.adapter = NotesAdapter(notes)
 binding.fab.setOnClickListener {
 val addNoteDialog = AddNoteDialogFragment()
 addNoteDialog.show(supportFragmentManager, "AddNoteDialog")
 }
 }
 override fun onCreateOptionsMenu(menu: Menu): Boolean {
 menuInflater.inflate(R.menu.menu_main, menu)
 return true
 }
 override fun onOptionsItemSelected(item: MenuItem): Boolean {
 return when (item.itemId) {
 R.id.action_add_note -> {
 val addNoteDialog = AddNoteDialogFragment()
 addNoteDialog.show(supportFragmentManager, "AddNoteDialog")
 true
 }
 R.id.action_view_notes -> {
 // Handle view notes action
 true
 }
 else -> super.onOptionsItemSelected(item)
 }
 }
 fun addNote(note: Note) {
 notes.add(note)
 binding.recyclerView.adapter?.notifyDataSetChanged()
 }
}
Addnote Fragnment
package com.example.notesapp
import android.os.Bundle
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.ArrayAdapter
import android.widget.Toast
import androidx.fragment.app.DialogFragment
import com.example.notesapp.databinding.FragmentAddNoteDialogBinding
class AddNoteDialogFragment : DialogFragment() {
 private var _binding: FragmentAddNoteDialogBinding? = null
 private val binding get() = _binding!!
 override fun onCreateView(
 inflater: LayoutInflater, container: ViewGroup?,
 savedInstanceState: Bundle?
 ): View? {
 _binding = FragmentAddNoteDialogBinding.inflate(inflater, container, false)
 return binding.root
 }
 override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
 super.onViewCreated(view, savedInstanceState)
 val categories = arrayOf("Work", "Personal", "Shopping", "Other")
 val adapter = ArrayAdapter(requireContext(), android.R.layout.simple_spinner_item, 
categories)
 
adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
 binding.spinnerCategory.adapter = adapter
 binding.btnAddNote.setOnClickListener {
 val title = binding.etTitle.text.toString()
 val content = binding.etContent.text.toString()
 val category = binding.spinnerCategory.selectedItem.toString()
 if (title.isNotEmpty() && content.isNotEmpty()) {
 val note = Note(title, content, category)
 (activity as MainActivity).addNote(note)
 dismiss()
 } else {
 Toast.makeText(requireContext(), "Please fill in all fields", 
Toast.LENGTH_SHORT).show()
 }
 }
 }
 override fun onDestroyView() {
 super.onDestroyView()
 _binding = null
 }
}
Adapter Class
package com.example.notesapp
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import androidx.recyclerview.widget.RecyclerView
import com.example.notesapp.databinding.ItemNoteBinding
class NotesAdapter(private val notes: List<Note>) : 
RecyclerView.Adapter<NotesAdapter.NoteViewHolder>() {
 override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): NoteViewHolder {
 val binding = ItemNoteBinding.inflate(LayoutInflater.from(parent.context), parent, 
false)
 return NoteViewHolder(binding)
 }
 override fun onBindViewHolder(holder: NoteViewHolder, position: Int) {
 val note = notes[position]
 holder.bind(note)
 }
 override fun getItemCount(): Int = notes.size
 class NoteViewHolder(private val binding: ItemNoteBinding) : 
RecyclerView.ViewHolder(binding.root) {
 fun bind(note: Note) {
 binding.tvTitle.text = note.title
 binding.tvContent.text = note.content
 binding.tvCategory.text = note.category
 }
 }
}
